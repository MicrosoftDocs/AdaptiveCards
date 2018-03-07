---
title: Android SDK
author: bekao
ms.author: bekao
ms.date: 09/27/2017
ms.topic: article
---

# Android library
This is a renderer which targets Android native controls.

## Create Adaptive Card Object Instance from JSON Text
```java
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.VERSION);
AdaptiveCard adaptiveCard = parseResult.GetAdaptiveCard();
```
## Render a card
```java
RenderedAdaptiveCard renderedCard = AdaptiveCardRenderer.getInstance().render(context, getSupportFragmentManager(), adaptiveCard, cardActionHandler, new HostConfig());
View v = renderedCard.getView();
```

### Card Action Handling

When a cards action is executed, the class that was passed to the render call that implements the ICardActionHandler interface gets invoked. Here is how to define your action handler:

```java
private void onSubmit(BaseActionElement actionElement, RenderedAdaptiveCard renderedAdaptiveCard)
{
    SubmitAction submitAction = null;
    if (actionElement instanceof SubmitAction) {
        submitAction = (SubmitAction) actionElement;
    } else if ((submitAction = SubmitAction.dynamic_cast(actionElement)) == null) {
        throw new InternalError("Unable to convert BaseActionElement to ShowCardAction object model.");
    }

    String data = submitAction.GetDataJson();
    Map<String, String> keyValueMap = renderedAdaptiveCard.getInputs();
    if (!data.isEmpty())
    {
        try {
            JSONObject object = new JSONObject(data);
            showToast("Submit data: " + object.toString() + "\nInput: " + keyValueMap.toString(), Toast.LENGTH_LONG);
        } catch (JSONException e) {
            showToast(e.toString(), Toast.LENGTH_LONG);
        }
    }
    else
    {
        showToast("Submit input: " + keyValueMap.toString(), Toast.LENGTH_LONG);
    }
}

private void onShowCard(BaseActionElement actionElement)
{
    ShowCardAction showCardAction = null;
    if (actionElement instanceof ShowCardAction)
    {
        showCardAction = (ShowCardAction) actionElement;
    }
    else if ((showCardAction = ShowCardAction.dynamic_cast(actionElement)) == null)
    {
        throw new InternalError("Unable to convert BaseActionElement to ShowCardAction object model.");
    }

    //Get the card from show card and create a view
    RenderedAdaptiveCard renderedCard = AdaptiveCardRenderer.getInstance().render(context, fragmentManager, showCardAction.GetCard(), cardActionHandler, hostConfig);

    ViewGroup viewGroup = (ViewGroup) renderedCard.getView();
    ...
}

private void onOpenUrl(BaseActionElement actionElement)
{
    OpenUrlAction openUrlAction = null;
    if (actionElement instanceof ShowCardAction)
    {
        openUrlAction = (OpenUrlAction) actionElement;
    }
    else if ((openUrlAction = OpenUrlAction.dynamic_cast(actionElement)) == null)
    {
        throw new InternalError("Unable to convert BaseActionElement to ShowCardAction object model.");
    }

    Intent browserIntent = new Intent(Intent.ACTION_VIEW, Uri.parse(openUrlAction.GetUrl()));
    this.startActivity(browserIntent);
}

public class ActionHandler implements ICardActionHandler
{
	@Override
    public void onAction(BaseActionElement actionElement, RenderedAdaptiveCard renderedCard)
    {
    	ActionType actionType = actionElement.GetElementType();
        if (actionType == ActionType.Submit)
        {
            onSubmit(actionElement, renderedCard);
        }
        else if (actionType == ActionType.ShowCard)
        {
            onShowCard(actionElement);
        }
        else if (actionType == ActionType.OpenUrl)
        {
            onOpenUrl(actionElement);
        }
        else if (actionType == ActionType.Custom)
        {
            //Handle activation of custom actions
            ...
        }
    }
}
```

### HostConfig 

To customize the renderer you provide an instance of the HostConfig object. (See [Host Config Schema](../HostConfig.md) for the full description.)

> The HostConfig object will be instantiated with defaults, so you can set just the properties you want to change.

> You may also create a HostConfig from a Json String
```java
HostConfig hostConfig = HostConfig.DeserializeFromString(hostConfigText);
```

### Custom Parsing of Card Elements

You may extend the parser to suport card elements that you have defined. For example, say we have a new element type that looks like this:
```json
{
	"type" : "MyType",
	"MyTypeData" : "My data"
}
```

Then the following lines demonstrate how to parse it into a CardElement that extends from the BaseCardElement:
```java
public class MyCustomCardElement extends BaseCardElement
{

    public MyCustomCardElement(CardElementType type) {
        super(type);
    }

    public String getMyTypeData()
    {
        return myTypeData;
    }

    public void setMyTypeData(String data)
    {
        myTypeData = data;
    }

    private String myTypeData;
}

public class MyCardElementParser extends BaseCardElementParser
{
    @Override
    public BaseCardElement Deserialize(ElementParserRegistration elementParserRegistration, ActionParserRegistration actionParserRegistration, JsonValue value)
    {
        MyCustomCardElement element = new CustomCardElement(CardElementType.Custom);
        element.SetElementTypeString("MyType");
        String val = value.getString();
        try {
            JSONObject obj = new JSONObject(val);
            element.setMyTypeData(obj.getString("secret"));
        } catch (JSONException e) {
            e.printStackTrace();
            element.setMyTypeData("Failed");
        }
        return element;
    }
}
```

And this is how to register the your parser and get an AdaptiveCard object containing the custom element:
```java
// Create an ElementParserRegistrationObject and add your parser to it
ElementParserRegistration elementParserRegistration = new ElementParserRegistration();
elementParserRegistration.AddParser("MyType", new MyCardElementParser());

AdaptiveCard adaptiveCard = AdaptiveCard.DeserializeFromString(jsonText, elementParserRegistration);
```

Next comes rendering the custom element

### Custom Rendering of Card Elements

To define our own custom renderer for our type, we must first create a class that extends from BaseCardElementParser:
```java
public class MyCardElementRenderer extends BaseCardElementRenderer
{
    @Override
    public View render(Context context, FragmentManager fragmentManager, ViewGroup viewGroup, BaseCardElement baseCardElement, Vector<IInputHandler> inputActionHandlerList, ICardActionHandler cardActionHandler, HostConfig hostConfig, ContainerStyle containerStyle) {

    	//Call findImplObj on baseCardElement to get the instace we returned at parse. We can then cast that object to our type
        CustomCardElement element = (CustomCardElement) baseCardElement.findImplObj();

        //Create some view and add it to the view group
        TextView textView = new TextView(context);
        textView.setText(element.getMyTypeData());
        textView.setAllCaps(true);
        viewGroup.addView(textView);

        //return the view
        return textView;
    }
}
```

We then register this renderer like so:
```java
CardRendererRegistration.getInstance().registerRenderer("blah", new CustomBlahRenderer());

RenderedAdaptiveCard renderedCard = AdaptiveCardRenderer.getInstance().render(context, getSupportFragmentManager(), adaptiveCard, cardActionHandler, new HostConfig());
```

