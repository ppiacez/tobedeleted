FORMAT: 1A
HOST: https://backoffice.predix.it/backoffice/v1/

# predixit

Api for predixit backoffice.

## Promotion Campaign Goals Collection [/campaign/promotion/goals]

### List All Promotion goals types [GET]
Retrieve all Promotions Goals with all the necessary attributes for rendering

+ Response 200 (application/json)

        {
            goals: [
                {
                    id: 1,
                    goal: 'Reward',
                    message: '<b>Reward your customers</b> with dedicated promotions, even when browsing without logging in, choose from the customers <b>who buy the most and those who spend more</b>.',
                    iconClass: 'fa fa-eye'
                }, {
                    id: 2,
                    goal: 'Stimulate',
                    message: '<b>Stimulate your customers</b> with dedicated promotions, even when browsing without logging in, choose from the customers <b>who abandon product in the cart or in checkout</b>.',
                    iconClass: 'fa fa-shopping-cart'
                
                }, {
                    id: 3,
                    goal: 'Get Back',
                    message: '<b>Get your customer</b> back with dedicated promotions, even when browsing without logging in, choose from the customers <b>who no longer but or add to cart or checkout</b>.',
                    iconClass: 'fa fa-line-chart'
                }
            ],
            statusCode: "OK",
            statusDescription: "message.success",
            warnings: []
        }

        

## Segments Collection By Goal [/campaign/promotion/goalSegments{?goal_id}]

+ Parameters
    + goal_id - Goal Id


### List Segments [GET]
Retrieve all goal's segments

+ Response 200 (application/json)

        {
            segments: [
                {
                    id: 1,
                    label: 'Who buy More'
                },{
                    id: 2,
                    label: 'Who spent More'
                }
            ],
            statusCode: "OK",
            statusDescription: "message.success",
            warnings: []
        }
        
        
## Dimensions Collection By Segment [/cluster/dimensions{?segment}]

+ Parameters
    + segment - Segment Id

### List Dimension [GET]
Get All Dimension by segment

+ Response 200 (application/json)

        {
            dimensions: [
                {
                    id: 1,
                    label: '1st Variable'
                },
                {
                    id: 1,
                    label: '2nd Variable'
                }
            ],
            statusCode: "OK",
            statusDescription: "message.success",
            warnings: []
        }

## Dimension Values Collection By Dimension [/cluster/dimensionValues{?dimension}]

+ Parameters
    + dimension - Dimension Id

### List Dimension Values [GET]
Get All Possibile Values by dimension

+ Response 200 (application/json)

        {
            dimensionValues: [
                {
                    id: 1,
                    label: '30 days'
                },
                {
                    id: 2,
                    label: '60 days'
                },
                {
                    id: 3,
                    label: '90 days'
                }
            ],
            statusCode: "OK",
            statusDescription: "message.success",
            warnings: []
        }
        
## Cluster  [/cluster/calculate]


### Calculate Cluster [POST]
Get Corrisponding cluster based on dimensions and values

+ Request (application/json)

        {
            data: [
                {
                    dimension: {dimensionId},
                    value: {valueId}
                },
                {
                    dimension: {dimensionId},
                    value: {valueId}
                }
            ]
        }

+ Response 200 (application/json)

        
        {
            cluster: {
                id: 1,
                label: 'Cluster X'
            },
            statusCode: "OK",
            statusDescription: "message.success",
            warnings: []
        }
        
        
## Template Catalog [/template/catalog]

### List All Default Templates [GET]
Get All default template with images for preview, and html template (base64)

+ Response 200 (application/json)

        {
            templates: [
                {
                    id: 1,
                    html: "cmFuZG9tc2Rmc2RmZ3NnZGFmc2dhYXdlcmd0YXdldGF3cnRhcnRlYXJ0d3R3dCA=",
                    thumbnail: "http://image.it/thumb_1.jpg",
                    preview: "http://image.it/preview_1.jpg"
                },
                {
                    dimension: 2,
                    value: "cmFuZG9tc2Rmc2RmZ3NnZGFmc2dhYXdlcmd0YXdldGF3cnRhcnRlYXJ0d3R3dCA=",
                    thumbnail: "http://image.it/thumb_2.jpg",
                    preview: "http://image.it/preview_2.jpg"
                }
            ],
            statusCode: "OK",
            statusDescription: "message.success",
            warnings: []
        }
        
## Template  [/template/{templateId}]

### Get Existing campaign template  [GET]
Create a new template and return id. 

+ Request (application/json)

        {
            template: {
                campaign: {campaignId},
                html: "<style></style><div></div>"
            }
        }

+ Response 200 (application/json)

        {
            template: 
                {   
                    id: {templateId},
                    campaign: {campaignId},
                    html: "cmFuZG9tc2Rmc2RmZ3NnZGFmc2dhYXdlcmd0YXdldGF3cnRhcnRlYXJ0d3R3dCA="
                }
            ,
            statusCode: "OK",
            statusDescription: "message.success",
            warnings: []
        }


### Modify existing campaign template [PUT]
Modify existing template. 

+ Request (application/json)

        {
            template: {
                id: {templateId},
                html: "<style></style><div></div>",
                position: "tl|tc|tr|mr|mc|ml|br|bc|bl"
            }
        }

+ Response 200 (application/json)

        {
            template: 
                {   
                    id: {templateId},
                    campaign: {campaignId},
                    html: "cmFuZG9tc2Rmc2RmZ3NnZGFmc2dhYXdlcmd0YXdldGF3cnRhcnRlYXJ0d3R3dCA=",
                    position: "tl|tc|tr|mr|mc|ml|br|bc|bl"
                }
            ,
            statusCode: "OK",
            statusDescription: "message.success",
            warnings: []
        }

## Template  [/template]


### Create new campaign template [POST]
Create a new template and return id. 

+ Request (application/json)

        {
            template: {
                campaign: {campaignId},
                html: "<style></style><div></div>",
                position: "tl|tc|tr|mr|mc|ml|br|bc|bl"
            }
        }

+ Response 200 (application/json)

        {
            template: 
                {   
                    id: {templateId},
                    campaign: {campaignId},
                    html: "cmFuZG9tc2Rmc2RmZ3NnZGFmc2dhYXdlcmd0YXdldGF3cnRhcnRlYXJ0d3R3dCA=",
                    position: "tl|tc|tr|mr|mc|ml|br|bc|bl"
                }
            ,
            statusCode: "OK",
            statusDescription: "message.success",
            warnings: []
        }
        
## Conditions Collection [/campaign/conditions]

### List Conditions [GET]
Retrieve all Conditions

+ Response 200 (application/json)

        {
            conditions: [
                {
                    id: 1,
                    label: 'Visitors who ﬁlled in or have already seen the following campaigns'
                },{
                    id: 2,
                    label: 'Returning or new visitors'
                }
            ],
            statusCode: "OK",
            statusDescription: "message.success",
            warnings: []
        }
        
## List Campaigns [/campaigns{?contractId}]

+ Parameters
    + contractId - Ecommerce Id

### List Campaigns [GET]
Get All Campaigns for a given ecommerce

+ Response 200 (application/json)

        {
            campaigns: {
                promotions: [
                    {
                        id: {promotionId},
                        contract: {contractId},
                        goal: {goalId}
                        name: "name",
                        priority: 1,
                        cluster: {clusterId},
                        catalogTemplate: {catalogId},
                        campaignTemplate: {templateId},
                        status: 'DRAFT|ACTIVE|INACTIVE',
                        conditions: [ {conditionId1} , {conditionId2}  ],
                        createdAt: "gg/mm/yyyy hh:MM:ss",
                        modifiedAt: "gg/mm/yyyy hh:MM:ss", 
                        startDatetime: "gg/mm/yyyy hh:MM:ss",
                        endDatetime: "gg/mm/yyyy hh:MM:ss",
                        ABTest: true,
                        APercentage: 60,
                        BPercentage: 40,
                        addToCart: 0,
                        sales: 0,
                        revenues: 0
                    }
                ]
            },
            statusCode: "OK",
            statusDescription: "message.success",
            warnings: []
        }
        
        
## promotion [/campaign/promotion]

### Create new promotion campaign  [POST]
Create a new promotion and return it. 

+ Request (application/json)

        {
            promotion: {
                contract: {contractId},
                goal: {goalId}
                name: "name",
                startDatetime: "gg/mm/yyyy hh:MM:ss",
                endDatetime: "gg/mm/yyyy hh:MM:ss",
            }
        }

+ Response 200 (application/json)

        {
            promotion: {
                id: {promotionId},
                contract: {contractId},
                goal: {goalId}
                name: "name",
                startDatetime: "gg/mm/yyyy hh:MM:ss",
                endDatetime: "gg/mm/yyyy hh:MM:ss",
            }
            ,
            statusCode: "OK",
            statusDescription: "message.success",
            warnings: []
        }
        
## Promotion [/campaigns/promotion/{promotionId}]

+ Parameters
    + promotionId - Promotion Id

### Promotion [GET]
Get a Promotion 

+ Response 200 (application/json)

        {
            promotion: {
                id: {promotionId},
                contract: {contractId},
                goal: {goalId}
                name: "name",
                priority: 1,
                cluster: {clusterId},
                catalogTemplate: {catalogId},
                campaignTemplate: {templateId},
                status: 'DRAFT|ACTIVE|INACTIVE',
                conditions: [ {conditionId1} , {conditionId2}  ],
                createdAt: "gg/mm/yyyy hh:MM:ss",
                modifiedAt: "gg/mm/yyyy hh:MM:ss", 
                startDatetime: "gg/mm/yyyy hh:MM:ss",
                endDatetime: "gg/mm/yyyy hh:MM:ss",
                ABTest: true,
                APercentage: 60,
                BPercentage: 40,
                addToCart: 0,
                sales: 0,
                revenues: 0
            },
            statusCode: "OK",
            statusDescription: "message.success",
            warnings: []
        }

### Modify Promotion [PUT]
Modify an existing Promotion (only if status <> 'ACTIVE')

+ Request (application/json)

        {
            promotion: 
                    {
                        id: {promotionId},
                        contract: {contractId},
                        goal: {goalId}
                        name: "name",
                        priority: 1,
                        cluster: {clusterId},
                        catalogTemplate: {catalogId},
                        campaignTemplate: {templateId},
                        conditions: [ {conditionId1} , {conditionId2}  ],
                        createdAt: "gg/mm/yy hh:MM:ss",
                        modifiedAt: "gg/mm/yy hh:MM:ss", 
                        startDatetime: "gg/mm/yy hh:MM:ss",
                        endDatetime: "gg/mm/yy hh:MM:ss",
                        ABTest: true,
                        APercentage: 60,
                        BPercentage: 40,
                    }
        }

+ Response 200 (application/json)

        {
            promotion: {
                id: {promotionId},
                contract: {contractId},
                goal: {goalId}
                name: "name",
                priority: 1,
                cluster: {clusterId},
                catalogTemplate: {catalogId},
                campaignTemplate: {templateId},
                status: 'DRAFT|ACTIVE|INACTIVE',
                conditions: [ {conditionId1} , {conditionId2}  ],
                createdAt: "gg/mm/yyyy hh:MM:ss",
                modifiedAt: "gg/mm/yyyy hh:MM:ss", 
                startDatetime: "gg/mm/yyyy hh:MM:ss",
                endDatetime: "gg/mm/yyyy hh:MM:ss",
                ABTest: true,
                APercentage: 60,
                BPercentage: 40,
                addToCart: 0,
                sales: 0,
                revenues: 0
            },
            statusCode: "OK",
            statusDescription: "message.success",
            warnings: []
        }
        
## Promotion [/campaigns/promotion/{promotionId}/wizard/stepOne]

+ Parameters
    + promotionId - Promotion Id

### Validate And Save Step One Data Promotion [PUT]
Cretion/Edit promotion Wizard step 1 (only if status <> 'ACTIVE')

+ Request (application/json)

        {
            promotion: 
                    {
                        id: {promotionId},
                        name: "name",
                        cluster: {clusterId},
                        catalogTemplate: {catalogId},
                        ABTest: true,
                        APercentage: 60,
                        BPercentage: 40
                    }
        }

+ Response 200 (application/json)

        {
            promotion: {
                id: {promotionId},
                contract: {contractId},
                goal: {goalId}
                name: "name",
                priority: 1,
                cluster: {clusterId},
                catalogTemplate: {catalogId},
                campaignTemplate: {templateId},
                status: 'DRAFT|ACTIVE|INACTIVE',
                conditions: [ {conditionId1} , {conditionId2}  ],
                createdAt: "gg/mm/yyyy hh:MM:ss",
                modifiedAt: "gg/mm/yyyy hh:MM:ss", 
                startDatetime: "gg/mm/yyyy hh:MM:ss",
                endDatetime: "gg/mm/yyyy hh:MM:ss",
                ABTest: true,
                APercentage: 60,
                BPercentage: 40,
                addToCart: 0,
                sales: 0,
                revenues: 0
            },
            statusCode: "OK",
            statusDescription: "message.success",
            warnings: []
        }

## Promotion [/campaigns/promotion/{promotionId}/wizard/stepTwo]

+ Parameters
    + promotionId - Promotion Id

### Validate And Save Step Two Data Promotion [PUT]
Cretion/Edit promotion Wizard step 2 (TEMPLATE) (only if status <> 'ACTIVE')

+ Request (application/json)

        {
            promotion: 
                    {
                        id: {promotionId},
                        campaignTemplate: {templateId},
                    }
        }

+ Response 200 (application/json)

        {
            promotion: {
                id: {promotionId},
                contract: {contractId},
                goal: {goalId}
                name: "name",
                priority: 1,
                cluster: {clusterId},
                catalogTemplate: {catalogId},
                campaignTemplate: {templateId},
                status: 'DRAFT|ACTIVE|INACTIVE',
                conditions: [ {conditionId1} , {conditionId2}  ],
                createdAt: "gg/mm/yyyy hh:MM:ss",
                modifiedAt: "gg/mm/yyyy hh:MM:ss", 
                startDatetime: "gg/mm/yyyy hh:MM:ss",
                endDatetime: "gg/mm/yyyy hh:MM:ss",
                ABTest: true,
                APercentage: 60,
                BPercentage: 40,
                addToCart: 0,
                sales: 0,
                revenues: 0
            },
            statusCode: "OK",
            statusDescription: "message.success",
            warnings: []
        }


## Promotion [/campaigns/promotion/{promotionId}/wizard/stepThree]

+ Parameters
    + promotionId - Promotion Id

### Validate And Save Step Three Data Promotion [PUT]
Cretion/Edit promotion Wizard step 3 (only if status <> 'ACTIVE')

+ Request (application/json)

        {
            promotion: 
                    {
                        id: {promotionId},
                        name: "name",
                        conditions: [ {conditionId1} , {conditionId2}  ],
                        startDatetime: "gg/mm/yy hh:MM:ss",
                        endDatetime: "gg/mm/yy hh:MM:ss",
                    }
        }

+ Response 200 (application/json)

        {
            promotion: {
                id: {promotionId},
                contract: {contractId},
                goal: {goalId}
                name: "name",
                priority: 1,
                cluster: {clusterId},
                catalogTemplate: {catalogId},
                campaignTemplate: {templateId},
                status: 'DRAFT|ACTIVE|INACTIVE',
                createdAt: "gg/mm/yyyy hh:MM:ss",
                modifiedAt: "gg/mm/yyyy hh:MM:ss", 
                startDatetime: "gg/mm/yyyy hh:MM:ss",
                endDatetime: "gg/mm/yyyy hh:MM:ss",
                ABTest: true,
                APercentage: 60,
                BPercentage: 40,
                addToCart: 0,
                sales: 0,
                revenues: 0
            },
            statusCode: "OK",
            statusDescription: "message.success",
            warnings: []
        }
        
## Promotion [/campaigns/promotion/{promotionId}/setActive]

+ Parameters
    + promotionId - Promotion Id

### Change Promotion Status Promotion [PUT]
Change Promotion Status

+ Request (application/json)

        {
            promotion: 
                    {
                        id: {promotionId},
                        active: true|false,
                    }
        }

+ Response 200 (application/json)

        {
            promotion: {
                id: {promotionId},
                contract: {contractId},
                goal: {goalId}
                name: "name",
                priority: 1,
                cluster: {clusterId},
                catalogTemplate: {catalogId},
                campaignTemplate: {templateId},
                status: 'DRAFT|ACTIVE|INACTIVE',
                createdAt: "gg/mm/yyyy hh:MM:ss",
                modifiedAt: "gg/mm/yyyy hh:MM:ss", 
                startDatetime: "gg/mm/yyyy hh:MM:ss",
                endDatetime: "gg/mm/yyyy hh:MM:ss",
                ABTest: true,
                APercentage: 60,
                BPercentage: 40,
                addToCart: 0,
                sales: 0,
                revenues: 0
            },
            statusCode: "OK",
            statusDescription: "message.success",
            warnings: []
        }

        

   

