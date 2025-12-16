---
title:  Sample of Expense Report
author: luywang
description: This page provides a sample code for Expense Report Cards.
ms.author: luywang
ms.date: 12/15/2025
ms.topic: concept-article
---

# Expense Report

> [!NOTE]
> **Are you building Copilot, Teams or Outlook scenarios powered by Adaptive Cards?**
> Visit [**Adaptive Card Documentation Hub**](https://adaptivecards.microsoft.com/), the new one-stop-shop for all your Adaptive Card needs! It has all the resources you're looking for, including complete documentation for many new features, such as [Responsive layout](https://adaptivecards.microsoft.com/?topic=responsive-layout), [Icon](https://adaptivecards.microsoft.com/?topic=Icon), [Badge](https://adaptivecards.microsoft.com/?topic=Badge), [Carousel](https://adaptivecards.microsoft.com/?topic=Carousel), [Charts](https://adaptivecards.microsoft.com/?topic=Chart.Line), and much more!



These samples are *just a teaser* of the type of cards you can create. Go ahead and tweak them to make any scenario possible\!

**Important note about accessibility:** In version 1.3 of the schema we introduced a **label** property on Inputs to improve accessibility. If the [Host app you are targeting](/adaptive-cards/resources/partners) supports v1.3 you should use **label** instead of a **TextBlock** as seen in some samples below. Once most Host apps have updated to the latest version we will update the samples accordingly.


## Expense report sample

The following section displays the JSON for an "Expense report" Adaptive Card sample, shown with and without templating.

### JSON Code (Without Templating)

**JSON**

```json
{
	"type": "AdaptiveCard",
	"body": [
		{
			"type": "Container",
			"style": "emphasis",
			"items": [
				{
					"type": "ColumnSet",
					"columns": [
						{
							"type": "Column",
							"items": [
								{
									"type": "TextBlock",
									"size": "large",
									"weight": "bolder",
									"text": "**EXPENSE APPROVAL**",
									"wrap": true,
									"style": "heading"
								}
							],
							"width": "stretch"
						},
						{
							"type": "Column",
							"items": [
								{
									"type": "Image",
									"url": "https://adaptivecards.io/content/pending.png",
									"height": "30px",
									"altText": "Pending"
								}
							],
							"width": "auto"
						}
					]
				}
			],
			"bleed": true
		},
		{
			"type": "Container",
			"items": [
				{
					"type": "ColumnSet",
					"columns": [
						{
							"type": "Column",
							"items": [
								{
									"type": "TextBlock",
									"size": "extraLarge",
									"text": "Trip to UAE",
									"wrap": true,
									"style": "heading"
								}
							],
							"width": "stretch"
						},
						{
							"type": "Column",
							"items": [
								{
									"type": "ActionSet",
									"actions": [
										{
											"type": "Action.OpenUrl",
											"title": "EXPORT AS PDF",
											"url": "https://adaptivecards.io"
										}
									]
								}
							],
							"width": "auto"
						}
					]
				},
				{
					"type": "TextBlock",
					"spacing": "small",
					"size": "small",
					"weight": "bolder",
					"text": "[ER-13052](https://adaptivecards.io)",
					"wrap": true
				},
				{
					"type": "FactSet",
					"spacing": "large",
					"facts": [
						{
							"title": "Submitted By",
							"value": "**Matt Hidinger** matt@contoso.com"
						},
						{
							"title": "Duration",
							"value": "2019/06/19 - 2019/06/25"
						},
						{
							"title": "Submitted On",
							"value": "2019/04/14"
						},
						{
							"title": "Reimbursable Amount",
							"value": "$ 404.30"
						},
						{
							"title": "Awaiting approval from",
							"value": "**Thomas** thomas@contoso.com"
						},
						{
							"title": "Submitted to",
							"value": "**David** david@contoso.com"
						}
					]
				}
			]
		},
		{
			"type": "Container",
			"spacing": "large",
			"style": "emphasis",
			"items": [
				{
					"type": "TextBlock",
					"weight": "bolder",
					"text": "EXPENSE DETAILS",
					"wrap": true
				}
			],
			"bleed": true
		},
		{
			"type": "ActionSet",
			"actions": [
				{
					"type": "Action.ShowCard",
					"title": "06/19: Air Travel Expense - $300",
					"card": {
						"type": "AdaptiveCard",
						"body": [
							{
								"type": "Container",
								"items": [
									{
										"type": "Container",
										"items": [
											{
												"type": "TextBlock",
												"text": "* Leg 1 on Tue, Jun 19th, 2019 at 6:00 AM.",
												"isSubtle": true,
												"wrap": true
											},
											{
												"type": "TextBlock",
												"text": "* Leg 2 on Tue, Jun 19th, 2019 at 7:15 PM.",
												"isSubtle": true,
												"wrap": true
											},
											{
												"type": "Container",
												"items": [
													{
														"type": "Input.Text",
														"id": "comment0",
														"label": "Add your comment here"
													}
												]
											}
										]
									},
									{
										"type": "Container",
										"items": [
											{
												"type": "ColumnSet",
												"columns": [
													{
														"type": "Column",
														"items": [
															{
																"type": "ActionSet",
																"actions": [
																	{
																		"type": "Action.Submit",
																		"title": "Send",
																		"data": {
																			"id": "_qkQW8dJlUeLVi7ZMEzYVw",
																			"action": "comment",
																			"lineItem": 1
																		}
																	}
																]
															}
														],
														"width": "auto"
													}
												]
											}
										]
									}
								]
							}
						]
					}
				}
			]
		},
		{
			"type": "ActionSet",
			"actions": [
				{
					"type": "Action.ShowCard",
					"title": "06/19: Auto Mobile Expense - $100",
					"card": {
						"type": "AdaptiveCard",
						"body": [
							{
								"type": "Container",
								"items": [
									{
										"type": "Container",
										"items": [
											{
												"type": "TextBlock",
												"text": "* Contoso Car Rentrals, Tues 6/19 at 7:00 AM",
												"isSubtle": true,
												"wrap": true
											},
											{
												"type": "Container",
												"items": [
													{
														"type": "Input.Text",
														"id": "comment1",
														"label": "Add your comment here"
													}
												]
											}
										]
									},
									{
										"type": "Container",
										"items": [
											{
												"type": "ColumnSet",
												"columns": [
													{
														"type": "Column",
														"items": [
															{
																"type": "ActionSet",
																"actions": [
																	{
																		"type": "Action.Submit",
																		"title": "Send",
																		"data": {
																			"id": "_qkQW8dJlUeLVi7ZMEzYVw",
																			"action": "comment",
																			"lineItem": 1
																		}
																	}
																]
															}
														],
														"width": "auto"
													}
												]
											}
										]
									}
								]
							}
						]
					}
				}
			]
		},
		{
			"type": "ActionSet",
			"actions": [
				{
					"type": "Action.ShowCard",
					"title": "06/21: Excess Baggage Cost - $4.30",
					"card": {
						"type": "AdaptiveCard",
						"body": [
							{
								"type": "Container",
								"items": [
									{
										"type": "Container",
										"items": [
											{
												"type": "Container",
												"items": [
													{
														"type": "Input.Text",
														"id": "comment2",
														"label": "Add your comment here"
													}
												]
											}
										]
									},
									{
										"type": "Container",
										"items": [
											{
												"type": "ColumnSet",
												"columns": [
													{
														"type": "Column",
														"items": [
															{
																"type": "ActionSet",
																"actions": [
																	{
																		"type": "Action.Submit",
																		"title": "Send",
																		"data": {
																			"id": "_qkQW8dJlUeLVi7ZMEzYVw",
																			"action": "comment",
																			"lineItem": 1
																		}
																	}
																]
															}
														],
														"width": "auto"
													}
												]
											}
										]
									}
								]
							}
						]
					}
				}
			]
		},
		{
			"type": "Table",
			"spacing": "large",
			"separator": true,
			"firstRowAsHeaders": false,
			"showGridLines": false,
			"columns": [
				{
					"width": 3
				},
				{
					"width": 1
				}
			],
			"rows": [
				{
					"type": "TableRow",
					"cells": [
						{
							"type": "TableCell",
							"items": [
								{
									"type": "TextBlock",
									"text": "Total Expense Amount",
									"horizontalAlignment": "right",
									"wrap": true
								}
							]
						},
						{
							"type": "TableCell",
							"items": [
								{
									"type": "TextBlock",
									"text": "404.30",
									"horizontalAlignment": "right",
									"wrap": true
								}
							]
						}
					]
				},
				{
					"type": "TableRow",
					"cells": [
						{
							"type": "TableCell",
							"items": [
								{
									"type": "TextBlock",
									"text": "Non-reimbursable Amount",
									"horizontalAlignment": "right",
									"wrap": true
								}
							]
						},
						{
							"type": "TableCell",
							"items": [
								{
									"type": "TextBlock",
									"text": "(-) 0.00",
									"horizontalAlignment": "right",
									"wrap": true
								}
							]
						}
					]
				},
				{
					"type": "TableRow",
					"cells": [
						{
							"type": "TableCell",
							"items": [
								{
									"type": "TextBlock",
									"text": "Advance Amount",
									"horizontalAlignment": "right",
									"wrap": true
								}
							]
						},
						{
							"type": "TableCell",
							"items": [
								{
									"type": "TextBlock",
									"text": "(-) 0.00",
									"horizontalAlignment": "right",
									"wrap": true
								}
							]
						}
					]
				}
			]
		},
		{
			"type": "Container",
			"style": "emphasis",
			"items": [
				{
					"type": "ColumnSet",
					"columns": [
						{
							"type": "Column",
							"items": [
								{
									"type": "TextBlock",
									"horizontalAlignment": "right",
									"text": "Amount to be Reimbursed",
									"wrap": true
								}
							],
							"width": "stretch"
						},
						{
							"type": "Column",
							"items": [
								{
									"type": "TextBlock",
									"weight": "bolder",
									"text": "$404.30",
									"wrap": true
								}
							],
							"width": "auto"
						},
						{
							"type": "Column",
							"width": "auto"
						}
					]
				}
			],
			"bleed": true
		},
		{
			"type": "ActionSet",
			"actions": [
				{
					"type": "Action.ShowCard",
					"title": "Show history",
					"card": {
						"type": "AdaptiveCard",
						"body": [
							{
								"type": "Container",
								"items": [
									{
										"type": "TextBlock",
										"text": "* Expense submitted by **Matt Hidinger** on {{DATE(2019-07-15T10:33:12+00:00, SHORT)}}",
										"isSubtle": true,
										"wrap": true
									},
									{
										"type": "TextBlock",
										"text": "* Expense approved by **Thomas** on {{DATE(2019-07-15T14:33:12+00:00, SHORT)}}",
										"isSubtle": true,
										"wrap": true
									}
								]
							}
						]
					}
				}
			]
		},
		{
			"type": "Container",
			"items": [
				{
					"type": "ActionSet",
					"actions": [
						{
							"type": "Action.Submit",
							"title": "Approve",
							"style": "positive",
							"data": {
								"id": "_qkQW8dJlUeLVi7ZMEzYVw",
								"action": "approve"
							}
						},
						{
							"type": "Action.ShowCard",
							"title": "Reject",
							"style": "destructive",
							"card": {
								"type": "AdaptiveCard",
								"body": [
									{
										"type": "Input.Text",
										"id": "RejectCommentID",
										"label": "Please specify an appropriate reason for rejection",
										"isMultiline": true,
										"isRequired": true,
										"errorMessage": "A reason for rejection is necessary"
									}
								],
								"actions": [
									{
										"type": "Action.Submit",
										"title": "Send",
										"data": {
											"id": "_qkQW8dJlUeLVi7ZMEzYVw",
											"action": "reject"
										}
									}
								],
								"$schema": "http://adaptivecards.io/schemas/adaptive-card.json"
							}
						}
					]
				}
			]
		}
	],
	"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
	"version": "1.5",
	"fallbackText": "This card requires Adaptive Cards v1.5 support to be rendered properly."
}
```

### JSON Code (With Templating)

**Data JSON**

```json
{
	"code": "ER-13052",
	"message": "success",
	"created_by_name": "Matt Hidinger",
	"created_date": "2019-07-15T18:33:12+0800",
	"submitted_date": "2019-04-14T18:33:12+0800",
	"creater_email": "matt@contoso.com",
	"status": "Pending",
	"status_url": "https://adaptivecards.io/content/pending.png",
	"approver": "Thomas",
	"purpose": "Trip to UAE",
	"approval_date": "2019-07-15T22:33:12+0800",
	"approver": "Thomas",
	"approver_email": "thomas@contoso.com",
	"other_submitter": "David",
	"other_submitter_email": "david@contoso.com",

	"expenses": [
		{
			"expense_id": "16367000000083065",
			"approver": "Thomas",
			"date": "2017-02-21",
			"description": "Air Travel Expense",
			"created_by": "636965431200000000",
			"created_by_name": "PATRICIA",
			"employee_number": "E001",
			"currency_id": "16367000000000097",
			"currency_code": "USD",
			"paid_through_account_id": "16367000000036003",
			"paid_through_account_name": "Employee Reimbursements",
			"bcy_total": 13900.79,
			"bcy_subtotal": 13900.79,
			"total": 300,
			"total_without_tax": 300,
			"is_billable": true,
			"is_reimbursable": true,
			"reference_number": "DD145",
			"due_days": "Due in 15 days",
			"merchant_id": "16367000000074027",
			"merchant_name": "ABS Solutions",
			"status": "approved",
			"created_time": "2019-06-19T18:33:12+0800",
			"last_modified_time": "2017-02-21T18:42:46+0530",
			"receipt_name": "receipt1.jpg",
			"report_id": "16367000000083075",
			"mileage_type": "non_mileage",
			"report_name": "Purchase",
			"is_receipt_only": false,
			"distance": 0,
			"per_diem_rate": 0,
			"per_diem_days": 0,
			"per_diem_id": "",
			"per_diem_name": "",
			"expense_type": "non_mileage",
			"location": "Washington",
			"receipt_type": "jpg",
			"policy_violated": false,
			"comments_count": 0,
			"report_status": "submitted",
			"price_precision": 2,
			"mileage_rate": 0,
			"mileage_unit": "km",
			"receipt_status": "processed",
			"is_uncategorized": false,
			"is_expired": false,
			"gl_code": "LG001",
			"exchange_rate": 66.943366,
			"start_reading": "",
			"end_reading": "",
			"payment_mode": "Check",
			"customer_id": "27927000000075081",
			"customer_name": "ACME Corp.",
			"custom_fields": [
				{
					"customfield_id": "16367000000277001",
					"label": "Other Name",
					"value": "Leg 1 on Tue, Jun 19th, 2019 at 6:00 AM."
				},
				{
					"customfield_id": "16367000000277001",
					"label": "Other Name",
					"value": "Leg 2 on Tue, Jun 19th, 2019 at 7:15 PM."
				}
			],
			"project_id": "27927000001243001",
			"project_name": "Coffee Research",
			"transaction_description": "",
			"tax_id": "16367000000086001",
			"tax_name": "Sales Tax",
			"tax_percentage": 2,
			"amount": 207.65,
			"is_inclusive_tax": false,
			"vehicle_type": "Bike",
			"vehicle_id": "17456000000078029",
			"fuel_type": "lpg",
			"engine_capacity_range": "between_1401cc_and_1600cc",
			"is_personal": false,
			"policy_id": "16367000000092011",
			"policy_name": "LIC",
			"documents": [
				{
					"file_name": "receipt1.jpg",
					"file_size_formatted": "71.8 KB",
					"attachment_order": 1,
					"document_id": "16367000000083071"
				}
			],
			"reimbursement_reference": "",
			"reimbursement_date": "",
			"reimbursement_paid_through_account_id": "",
			"reimbursement_paid_through_account_name": "",
			"reimbursement_currency_id": "",
			"reimbursement_currency_code": ""
		},
		{
			"expense_id": "16367000000083065",
			"date": "2019-06-19",
			"description": "Auto Mobile Expense",
			"created_by": "636965431200000000",
			"created_by_name": "PATRICIA",
			"employee_number": "E001",
			"currency_id": "16367000000000097",
			"currency_code": "USD",
			"paid_through_account_id": "16367000000036003",
			"paid_through_account_name": "Employee Reimbursements",
			"bcy_total": 13900.79,
			"bcy_subtotal": 13900.79,
			"total": 100,
			"total_without_tax": 100,
			"is_billable": true,
			"is_reimbursable": true,
			"reference_number": "DD145",
			"due_days": "Due in 15 days",
			"merchant_id": "16367000000074027",
			"merchant_name": "ABS Solutions",
			"status": "submitted",
			"created_time": "2019-06-19T18:33:12+0800",
			"last_modified_time": "2017-02-21T18:42:46+0530",
			"receipt_name": "receipt1.jpg",
			"report_id": "16367000000083075",
			"mileage_type": "non_mileage",
			"report_name": "Purchase",
			"is_receipt_only": false,
			"distance": 0,
			"per_diem_rate": 0,
			"per_diem_days": 0,
			"per_diem_id": "",
			"per_diem_name": "",
			"expense_type": "non_mileage",
			"location": "Washington",
			"receipt_type": "jpg",
			"policy_violated": false,
			"comments_count": 0,
			"report_status": "submitted",
			"price_precision": 2,
			"mileage_rate": 0,
			"mileage_unit": "km",
			"receipt_status": "processed",
			"is_uncategorized": false,
			"is_expired": false,
			"gl_code": "LG001",
			"exchange_rate": 66.943366,
			"start_reading": "",
			"end_reading": "",
			"payment_mode": "Check",
			"customer_id": "27927000000075081",
			"customer_name": "ACME Corp.",
			"custom_fields": [
				{
					"customfield_id": "16367000000277001",
					"label": "Other Name",
					"value": " Contoso Car Rentrals, Tues 6/19 at 7:00 AM"
				}
			],
			"project_id": "27927000001243001",
			"project_name": "Coffee Research",
			"transaction_description": "",
			"tax_id": "16367000000086001",
			"tax_name": "Sales Tax",
			"tax_percentage": 2,
			"amount": 207.65,
			"is_inclusive_tax": false,
			"vehicle_type": "Bike",
			"vehicle_id": "17456000000078029",
			"fuel_type": "lpg",
			"engine_capacity_range": "between_1401cc_and_1600cc",
			"is_personal": false,
			"policy_id": "16367000000092011",
			"policy_name": "LIC",
			"documents": [
				{
					"file_name": "receipt1.jpg",
					"file_size_formatted": "71.8 KB",
					"attachment_order": 1,
					"document_id": "16367000000083071"
				}
			],
			"reimbursement_reference": "",
			"reimbursement_date": "",
			"reimbursement_paid_through_account_id": "",
			"reimbursement_paid_through_account_name": "",
			"reimbursement_currency_id": "",
			"reimbursement_currency_code": ""
		},
		{
			"expense_id": "16367000000083065",
			"date": "2019-06-21",
			"description": "Excess Baggage Cost",
			"created_by": "636967159200000000",
			"created_by_name": "PATRICIA",
			"employee_number": "E001",
			"currency_id": "16367000000000097",
			"currency_code": "USD",
			"paid_through_account_id": "16367000000036003",
			"paid_through_account_name": "Employee Reimbursements",
			"bcy_total": 13900.79,
			"bcy_subtotal": 13900.79,
			"total": 50.38,
			"total_without_tax": 4.3,
			"is_billable": true,
			"is_reimbursable": false,
			"reference_number": "DD145",
			"due_days": "Due in 15 days",
			"merchant_id": "16367000000074027",
			"merchant_name": "ABS Solutions",
			"status": "submitted",
			"created_time": "2019-06-21T18:33:12+0800",
			"last_modified_time": "2017-02-21T18:42:46+0530",
			"receipt_name": "receipt1.jpg",
			"report_id": "16367000000083075",
			"mileage_type": "non_mileage",
			"report_name": "Purchase",
			"is_receipt_only": false,
			"distance": 0,
			"per_diem_rate": 0,
			"per_diem_days": 0,
			"per_diem_id": "",
			"per_diem_name": "",
			"expense_type": "non_mileage",
			"location": "Washington",
			"receipt_type": "jpg",
			"policy_violated": false,
			"comments_count": 0,
			"report_status": "submitted",
			"price_precision": 2,
			"mileage_rate": 0,
			"mileage_unit": "km",
			"receipt_status": "processed",
			"is_uncategorized": false,
			"is_expired": false,
			"gl_code": "LG001",
			"exchange_rate": 66.943366,
			"start_reading": "",
			"end_reading": "",
			"payment_mode": "Check",
			"customer_id": "27927000000075081",
			"customer_name": "ACME Corp.",
			"custom_fields": [],
			"project_id": "27927000001243001",
			"project_name": "Coffee Research",
			"transaction_description": "",
			"tax_id": "16367000000086001",
			"tax_name": "Sales Tax",
			"tax_percentage": 2,
			"amount": 207.65,
			"is_inclusive_tax": false,
			"vehicle_type": "Bike",
			"vehicle_id": "17456000000078029",
			"fuel_type": "lpg",
			"engine_capacity_range": "between_1401cc_and_1600cc",
			"is_personal": false,
			"policy_id": "16367000000092011",
			"policy_name": "LIC",
			"documents": [
				{
					"file_name": "receipt1.jpg",
					"file_size_formatted": "71.8 KB",
					"attachment_order": 1,
					"document_id": "16367000000083071"
				}
			],
			"reimbursement_reference": "",
			"reimbursement_date": "",
			"reimbursement_paid_through_account_id": "",
			"reimbursement_paid_through_account_name": "",
			"reimbursement_currency_id": "",
			"reimbursement_currency_code": ""
		}
	]
}
```

**Template JSON**

```json
{
	"type": "AdaptiveCard",
	"body": [
		{
			"type": "Container",
			"style": "emphasis",
			"items": [
				{
					"type": "ColumnSet",
					"columns": [
						{
							"type": "Column",
							"items": [
								{
									"type": "TextBlock",
									"size": "large",
									"weight": "bolder",
									"text": "**EXPENSE APPROVAL**",
									"style": "heading",
									"wrap": true
								}
							],
							"width": "stretch"
						},
						{
							"type": "Column",
							"items": [
								{
									"type": "Image",
									"url": "${status_url}",
									"altText": "${status}",
									"height": "30px"
								}
							],
							"width": "auto"
						}
					]
				}
			],
			"bleed": true
		},
		{
			"type": "Container",
			"items": [
				{
					"type": "ColumnSet",
					"columns": [
						{
							"type": "Column",
							"items": [
								{
									"type": "TextBlock",
									"size": "extraLarge",
									"text": "${purpose}",
									"wrap": true,
									"style": "heading"
								}
							],
							"width": "stretch"
						},
						{
							"type": "Column",
							"items": [
								{
									"type": "ActionSet",
									"actions": [
										{
											"type": "Action.OpenUrl",
											"title": "EXPORT AS PDF",
											"url": "https://adaptivecards.io"
										}
									]
								}
							],
							"width": "auto"
						}
					]
				},
				{
					"type": "TextBlock",
					"spacing": "small",
					"size": "small",
					"weight": "bolder",
					"text": "[${code}](https://adaptivecards.io)",
					"wrap": true
				},
				{
					"type": "FactSet",
					"spacing": "large",
					"facts": [
						{
							"title": "Submitted By",
							"value": "**${created_by_name}** ${creater_email}"
						},
						{
							"title": "Duration",
							"value": "${formatTicks(min(select(expenses, x, int(x.created_by))), 'yyyy-MM-dd')} - ${formatTicks(max(select(expenses, x, int(x.created_by))), 'yyyy-MM-dd')}"
						},
						{
							"title": "Submitted On",
							"value": "${formatDateTime(submitted_date, 'yyyy-MM-dd')}"
						},
						{
							"title": "Reimbursable Amount",
							"value": "$${formatNumber(sum(select(expenses, x, if(x.is_reimbursable, x.total, 0))), 2)}"
						},
						{
							"title": "Awaiting approval from",
							"value": "**${approver}** ${approver_email}"
						},
						{
							"title": "Submitted to",
							"value": "**${other_submitter}** ${other_submitter_email}"
						}
					]
				}
			]
		},
		{
			"type": "Container",
			"spacing": "large",
			"style": "emphasis",
			"items": [
				{
					"type": "TextBlock",
					"weight": "bolder",
					"text": "EXPENSE DETAILS",
					"wrap": true
				}
			],
			"bleed": true
		},
		{
			"type": "ActionSet",
			"$data": "${expenses}",
			"actions": [
				{
					"type": "Action.ShowCard",
					"title": "${formatDateTime(created_time, 'MM-dd')}: ${description} - $${formatNumber(total, 2)}",
					"card": {
						"type": "AdaptiveCard",
						"body": [
							{
								"type": "Container",
								"items": [
									{
										"type": "Container",
										"items": [
											{
												"$data": "${custom_fields}",
												"type": "TextBlock",
												"text": "* ${value}",
												"isSubtle": true,
												"wrap": true
											},
											{
												"type": "Container",
												"items": [
													{
														"type": "Input.Text",
														"id": "comment${$index}",
														"label": "Add your comment here"
													}
												]
											}
										]
									},
									{
										"type": "Container",
										"items": [
											{
												"type": "ColumnSet",
												"columns": [
													{
														"type": "Column",
														"items": [
															{
																"type": "ActionSet",
																"actions": [
																	{
																		"type": "Action.Submit",
																		"title": "Send",
																		"data": {
																			"id": "_qkQW8dJlUeLVi7ZMEzYVw",
																			"action": "comment",
																			"lineItem": 1
																		}
																	}
																]
															}
														],
														"width": "auto"
													}
												]
											}
										]
									}
								]
							}
						]
					}
				}
			]
		},
		{
			"type": "ColumnSet",
			"spacing": "large",
			"separator": true,
			"columns": [
				{
					"type": "Column",
					"items": [
						{
							"type": "TextBlock",
							"horizontalAlignment": "right",
							"text": "Total Expense Amount \t",
							"wrap": true
						},
						{
							"type": "TextBlock",
							"horizontalAlignment": "right",
							"text": "Non-reimbursable Amount",
							"wrap": true
						},
						{
							"type": "TextBlock",
							"horizontalAlignment": "right",
							"text": "Advance Amount",
							"wrap": true
						}
					],
					"width": "stretch"
				},
				{
					"type": "Column",
					"items": [
						{
							"type": "TextBlock",
							"text": "$${formatNumber(sum(select(expenses, x, x.total)), 2)}",
							"wrap": true
						},
						{
							"type": "TextBlock",
							"text": "(-) $${formatNumber(sum(select(expenses, x, if(x.is_reimbursable, 0, x.total))), 2)} \t",
							"wrap": true
						},
						{
							"type": "TextBlock",
							"text": "(-) 0.00 \t",
							"wrap": true
						}
					],
					"width": "auto"
				},
				{
					"type": "Column",
					"width": "auto"
				}
			]
		},
		{
			"type": "Container",
			"style": "emphasis",
			"items": [
				{
					"type": "ColumnSet",
					"columns": [
						{
							"type": "Column",
							"items": [
								{
									"type": "TextBlock",
									"horizontalAlignment": "right",
									"text": "Amount to be Reimbursed",
									"wrap": true
								}
							],
							"width": "stretch"
						},
						{
							"type": "Column",
							"items": [
								{
									"type": "TextBlock",
									"weight": "bolder",
									"text": "$${formatNumber(sum(select(expenses, x, if(x.is_reimbursable, x.total, 0))), 2)}",
									"wrap": true
								}
							],
							"width": "auto"
						},
						{
							"type": "Column",
							"width": "auto"
						}
					]
				}
			],
			"bleed": true
		},
		{
			"type": "ActionSet",
			"actions": [
				{
					"type": "Action.ShowCard",
					"title": "Show history",
					"card": {
						"type": "AdaptiveCard",
						"body": [
							{
								"type": "Container",
								"items": [
									{
										"type": "TextBlock",
										"text": "* Expense submitted by **${created_by_name}** on {{DATE(${formatDateTime(created_date, 'yyyy-MM-ddTHH:mm:ssZ')}, SHORT)}}",
										"isSubtle": true,
										"wrap": true
									},
									{
										"type": "TextBlock",
										"text": "* Expense ${expenses[0].status} by **${expenses[0].approver}** on {{DATE(${formatDateTime(approval_date, 'yyyy-MM-ddTHH:mm:ssZ')}, SHORT)}}",
										"isSubtle": true,
										"wrap": true
									}
								]
							}
						]
					}
				}
			]
		},
		{
			"type": "Container",
			"items": [
				{
					"type": "ActionSet",
					"actions": [
						{
							"type": "Action.Submit",
							"title": "Approve",
							"style": "positive",
							"data": {
								"id": "_qkQW8dJlUeLVi7ZMEzYVw",
								"action": "approve"
							}
						},
						{
							"type": "Action.ShowCard",
							"title": "Reject",
							"style": "destructive",
							"card": {
								"type": "AdaptiveCard",
								"body": [
									{
										"type": "Input.Text",
										"id": "RejectCommentID",
										"label": "Please specify an appropriate reason for rejection",
										"isMultiline": true,
										"isRequired": true,
										"errorMessage": "A reason for rejection is necessary"
									}
								],
								"actions": [
									{
										"type": "Action.Submit",
										"title": "Send",
										"data": {
											"id": "_qkQW8dJlUeLVi7ZMEzYVw",
											"action": "reject"
										}
									}
								],
								"$schema": "http://adaptivecards.io/schemas/adaptive-card.json"
							}
						}
					]
				}
			]
		}
	],
	"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
	"version": "1.5",
	"fallbackText": "This card requires Adaptive Cards v1.5 support to be rendered properly."
}
```

