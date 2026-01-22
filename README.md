# Loyalty Page API Contracts 

---

## APIs

- [Loyalty Skeleton](#1-loyalty-skeleton)
- [Loyalty Header](#2-loyalty-header)
- [Loyalty Brew Journey](#4-loyalty-brew-journey)
- [Unlocked Loyalty Benefits](#5-unlocked-loyalty-benefits)
- [Locked Loyalty Benefits](#6-locked-loyalty-benefits)
- [Loyalty FAQ](#6-loyalty-faq)
- [Loyalty Progress Widget for App Scan Bottom Sheet](#7-loyalty-progress-widget-for-app-scan-bottom-sheet)

---

## Tier Enum

```json
"PARTNER"
"INFLUENCER"
"AMBASSADOR"
```

---

## 1. Loyalty Skeleton

Returns widget skeleton configuration for loading states.

**URL:** `/api/v1/loyalty/skeleton`

**Method:** `GET`

### Response Body (Success)


For PARTNER

```json
{
  "meta": {
    "request_id": "550e8400-e29b-41d4-a716-446655440000",
    "timestamp": "2026-01-21T14:32:00Z",
    "version": "1.0",
    "end_point": "/api/v1/loyalty/skeleton",
    "cacheable": true
  },
  "data": {
    "skeleton": [
      {
        "widget_name": "loyalty_header",
        "view_type": "header_card"
      },
      {
        "widget_name": "brew_journey_status",
        "view_type": "stepper_card"
      },
      {
        "widget_name": "locked_tier_benefits", 
        "view_type": "grid_layout" 
      },
      {
        "widget_name": "loyalty_faqs",
        "view_type": "accordion_list"
      }
    ]
  }
}
```

For INFLUENCER

```json
{
  "meta": {
    "request_id": "550e8400-e29b-41d4-a716-446655440000",
    "timestamp": "2026-01-21T14:32:00Z",
    "version": "1.0",
    "end_point": "/api/v1/loyalty/skeleton",
    "cacheable": true
  },
  "data": {
    "skeleton": [
      {
        "widget_name": "loyalty_header",
        "view_type": "header_card"
      },
      {
        "widget_name": "unlocked_tier_benefits", 
        "view_type": "carousel" 
      },
      {
        "widget_name": "locked_tier_benefits", 
        "view_type": "grid_layout" 
      },
      {
        "widget_name": "loyalty_faqs",
        "view_type": "accordion_list"
      }
    ]
  }
}
```

For AMBASSADOR

```json
{
  "meta": {
    "request_id": "550e8400-e29b-41d4-a716-446655440000",
    "timestamp": "2026-01-21T14:32:00Z",
    "version": "1.0",
    "end_point": "/api/v1/loyalty/skeleton",
    "cacheable": true
  },
  "data": {
    "skeleton": [
      {
        "widget_name": "loyalty_header",
        "view_type": "header_card"
      },
      {
        "widget_name": "unlocked_tier_benefits", 
        "view_type": "carousel" 
      },
      {
        "widget_name": "loyalty_faqs",
        "view_type": "accordion_list"
      }
    ]
  }
}
```

---

## 2. Loyalty Header

Returns user profile and current tier information for the page header.

**URL:** `/api/v1/loyalty/header`

**Method:** `GET`

### Response Body (Success) - Partner

```json
{
  "meta": {
    "request_id": "550e8400-e29b-41d4-a716-446655440001",
    "timestamp": "2026-01-21T14:32:00Z",
    "version": "1.0",
    "end_point": "/api/v1/loyalty/header",
    "cacheable": false
  },
  "data": {
    "tier": {
      "current": "PARTNER",
      "displayName": "Partner",
      "image": {
        "url": "https://cdn.waveapp.com/avatars/partner.png"
      },
      "bgColor": ["#AC6069", "#EC8893"]
    },
    "progression": {
      "totalOrderCount": 3,
      "currentTierOrderCount": 3,
      "progressMessage": "3 orders away from becoming an Influencer",
      "progressPercentage": 50,
      "isMaxTier": false,
      "milestones": [
        {
          "tier": "PARTNER",
          "orderThreshold": 6,
          "cumulativeThreshold": 6,
          "displayLabel": "Partner",
          "status": "CURRENT",
          "badgeType": "PROGRESS",
          "badgeText": "3/6",
          "orderCountDisplay": "3 orders / 37 days",
          "ordersInTier": 3,
          "ordersNeeded": 6,
          "daysInTier": 37,
          "progressInTier": 50
        },
        {
          "tier": "INFLUENCER",
          "orderThreshold": 6,
          "cumulativeThreshold": 12,
          "displayLabel": "Influencer",
          "status": "LOCKED",
          "badgeType": "PROGRESS",
          "badgeText": "0/6",
          "orderCountDisplay": null,
          "ordersInTier": 0,
          "ordersNeeded": 6,
          "daysInTier": null,
          "progressInTier": 0
        },
        {
          "tier": "AMBASSADOR",
          "orderThreshold": null,
          "cumulativeThreshold": 12,
          "displayLabel": "Ambassador",
          "status": "LOCKED",
          "badgeType": "NONE",
          "badgeText": null,
          "orderCountDisplay": null,
          "ordersInTier": 0,
          "ordersNeeded": null,
          "daysInTier": null,
          "progressInTier": 0
        }
      ]
    },
    "cycle": {
      "startDate": "2025-12-15T00:00:00Z",
      "endDate": "2026-03-15T00:00:00Z",
      "daysRemaining": 53,
      "totalDays": 90,
      "maintenanceMessage": "Make 15 Orders by 9 March, to maintain this level.",
      "ordersForMaintenance": 15,
      "currentCycleOrders": 3,
      "isMigrationCycle": false
    }
  }
}
```

### Response Body (Success) - Influencer

```json
{
  "meta": {
    "request_id": "550e8400-e29b-41d4-a716-446655440002",
    "timestamp": "2026-01-21T14:32:00Z",
    "version": "1.0",
    "end_point": "/api/v1/loyalty/header",
    "cacheable": false
  },
  "data": {
    "tier": {
      "current": "INFLUENCER",
      "displayName": "Influencer",
      "image": {
        "url": "https://cdn.waveapp.com/avatars/influencer.png"
      },
      "bgColor": ["#7B68AE", "#9B8AC4"]
    },
    "progression": {
      "totalOrderCount": 9,
      "currentTierOrderCount": 3,
      "progressMessage": "3 orders away from becoming an Ambassador",
      "progressPercentage": 50,
      "isMaxTier": false,
      "milestones": [
        {
          "tier": "PARTNER",
          "orderThreshold": 6,
          "cumulativeThreshold": 6,
          "displayLabel": "Partner",
          "status": "COMPLETED",
          "badgeType": "CHECKMARK",
          "badgeText": null,
          "orderCountDisplay": null,
          "ordersInTier": 6,
          "ordersNeeded": 6,
          "daysInTier": null,
          "progressInTier": 100
        },
        {
          "tier": "INFLUENCER",
          "orderThreshold": 6,
          "cumulativeThreshold": 12,
          "displayLabel": "Influencer",
          "status": "CURRENT",
          "badgeType": "PROGRESS",
          "badgeText": "3/6",
          "orderCountDisplay": "3 orders / 24 days",
          "ordersInTier": 3,
          "ordersNeeded": 6,
          "daysInTier": 24,
          "progressInTier": 50
        },
        {
          "tier": "AMBASSADOR",
          "orderThreshold": null,
          "cumulativeThreshold": 12,
          "displayLabel": "Ambassador",
          "status": "LOCKED",
          "badgeType": "NONE",
          "badgeText": null,
          "orderCountDisplay": null,
          "ordersInTier": 0,
          "ordersNeeded": null,
          "daysInTier": null,
          "progressInTier": 0
        }
      ]
    },
    "cycle": {
      "startDate": "2025-12-15T00:00:00Z",
      "endDate": "2026-03-15T00:00:00Z",
      "daysRemaining": 53,
      "totalDays": 90,
      "maintenanceMessage": "Make 15 Orders by 9 March, to maintain this level.",
      "ordersForMaintenance": 15,
      "currentCycleOrders": 9,
      "isMigrationCycle": false
    }
  }
}
```

### Response Body (Success) - Ambassador

```json
{
  "meta": {
    "request_id": "550e8400-e29b-41d4-a716-446655440003",
    "timestamp": "2026-01-21T14:32:00Z",
    "version": "1.0",
    "end_point": "/api/v1/loyalty/header",
    "cacheable": false
  },
  "data": {
    "tier": {
      "current": "AMBASSADOR",
      "displayName": "Ambassador",
      "image": {
        "url": "https://cdn.waveapp.com/avatars/ambassador.png"
      },
      "bgColor": ["#2D8B6F", "#4AAD8C"]
    },
    "progression": {
      "totalOrderCount": 14,
      "currentTierOrderCount": 2,
      "progressMessage": "More than 12 orders within the 90-day cycle",
      "progressPercentage": 100,
      "isMaxTier": true,
      "milestones": [
        {
          "tier": "PARTNER",
          "orderThreshold": 6,
          "cumulativeThreshold": 6,
          "displayLabel": "Partner",
          "status": "COMPLETED",
          "badgeType": "CHECKMARK",
          "badgeText": null,
          "orderCountDisplay": null,
          "ordersInTier": 6,
          "ordersNeeded": 6,
          "daysInTier": null,
          "progressInTier": 100
        },
        {
          "tier": "INFLUENCER",
          "orderThreshold": 6,
          "cumulativeThreshold": 12,
          "displayLabel": "Influencer",
          "status": "COMPLETED",
          "badgeType": "CHECKMARK",
          "badgeText": null,
          "orderCountDisplay": null,
          "ordersInTier": 6,
          "ordersNeeded": 6,
          "daysInTier": null,
          "progressInTier": 100
        },
        {
          "tier": "AMBASSADOR",
          "orderThreshold": null,
          "cumulativeThreshold": 12,
          "displayLabel": "Ambassador",
          "status": "CURRENT",
          "badgeType": "CHECKMARK",
          "badgeText": null,
          "orderCountDisplay": "12+ orders / 90 days",
          "ordersInTier": 2,
          "ordersNeeded": null,
          "daysInTier": 90,
          "progressInTier": 100
        }
      ]
    },
    "cycle": {
      "startDate": "2025-12-15T00:00:00Z",
      "endDate": "2026-03-15T00:00:00Z",
      "daysRemaining": 53,
      "totalDays": 90,
      "maintenanceMessage": "Make 15 Orders by 9 March, to maintain this level.",
      "ordersForMaintenance": 15,
      "currentCycleOrders": 14,
      "isMigrationCycle": false
    }
  }
}
```

---

## 4. Loyalty Brew Journey

**URL:** `/api/v2/homepage/get-data/type=new-user-journey`

**Method:** `GET`

```json
{
  "meta": {
    "request_id": "550e8400-e29b-41d4-a716-446655440000",
    "timestamp": "2024-03-21T14:32:00Z",
    "version": "1.0",
    "end_point": "/api/v2/cart/receiver-details"
  },
  "data" : {
    "title": "Complete 5 orders in 30 days using \n Third Wave app to win an exclusive reward!",
    //below milestore layout, if it is null hide it
    "message_details": {
        "message":"Eligible for orders above ₹399 only",
        "style": {
            "text_color": "#145738"
        }
    },
    // style is for setting background of widget, if bg_image is present render else use bg_color
    "style": {
        "bg_color": "#dbefd7",
        "bg_image": {
            "url": "bg_image.png"
        },
        "progress_color": "#4db436",
        "dotted_line_color": "#656060"
    },
    "info": {
        "cta_text": "Know More",
        "title":"Offer Name",
        "summary_list": [{
          "message": "Rule 1"
        }]
    },
    "tick_image": {
        "url": "tick_img.png"
    },
    "current_progress": 3,
    "total_steps": 5,
    "steps": [
        {
            "message": "Almost there",
            "status":"completed", //up-coming, in-queue
            "image": {
                "url": "img.png"
            }
        }
    ]
  }
}
```

Refer this more

https://github.com/TWC-HBPL/twc-tech-docs/blob/master/api_contracts/home-install-uninstall.md

---

## 5. Unlocked Loyalty Benefits

**URL:** `/api/v1/loyalty/unlocked-benefits`

**Method:** `GET`

### Response Body (Success) - Influencer

```json
{
  "meta": {
    "request_id": "550e8400-e29b-41d4-a716-446655440011",
    "timestamp": "2026-01-21T14:32:00Z",
    "version": "1.0",
    "end_point": "/api/v1/loyalty/unlocked-benefits",
    "cacheable": false
  },
  "data": {
    "title": "Influencer Benefits",
    "sub_title": "Your exclusive perks as an influencer",
    "tierBenefits": [
      {
        "title": "Referral Discount",
        "title_color": "#FFFFFF",
        "image": "https://cdn.waveapp.com/icons/birthday-coffee.png",
        "tag": {
          "label": "Unlimited",
          "bg_color": "#535388",
          "text_color": "#FFFFFF"
        }
      },
      {
        "title": "1 Free Coffee",
        "title_color": "#FFFFFF",
        "image": "https://cdn.waveapp.com/icons/birthday-coffee.png",
        "tag": {
          "label": "Claimed",
          "bg_color": "#535388",
          "text_color": "#FFFFFF"
        }
      },
      {
        "title": "1 Free Coffee",
        "title_color": "#FFFFFF",
        "image": "https://cdn.waveapp.com/icons/birthday-coffee.png",
        "tag": null
      }
    ]
  }
}
```

### Response Body (Success) - Ambassador

```json
{
  "meta": {
    "request_id": "550e8400-e29b-41d4-a716-446655440011",
    "timestamp": "2026-01-21T14:32:00Z",
    "version": "1.0",
    "end_point": "/api/v1/loyalty/unlocked-benefits",
    "cacheable": false
  },
  "data": {
    "title": "Influencer Benefits",
    "sub_title": "Your exclusive perks as an influencer",
    "tierBenefits": [
      {
        "title": "Referral Discount",
        "title_color": "#FFFFFF",
        "image": "https://cdn.waveapp.com/icons/birthday-coffee.png",
        "tag": {
          "label": "Unlimited",
          "bg_color": "#535388",
          "text_color": "#FFFFFF"
        }
      },
      {
        "title": "1 Free Coffee",
        "title_color": "#FFFFFF",
        "image": "https://cdn.waveapp.com/icons/birthday-coffee.png",
        "tag": {
          "label": "Claimed",
          "bg_color": "#535388",
          "text_color": "#FFFFFF"
        }
      },
      {
        "title": "1 Free Coffee",
        "title_color": "#FFFFFF",
        "image": "https://cdn.waveapp.com/icons/birthday-coffee.png",
        "tag": null
      }
    ]
  }
}
```

### Response Body (Success) - Partner

```json
{
  "meta": {
    "request_id": "550e8400-e29b-41d4-a716-446655440011",
    "timestamp": "2026-01-21T14:32:00Z",
    "version": "1.0",
    "end_point": "/api/v1/loyalty/unlocked-benefits",
    "cacheable": false
  },
  "data": {
    "title":"Influencer Benefits",
    "sub_title":"Your exclusive perks as an influencer",
    "tierBenefits": [
    {
      "title": "Referral Discount",
      "tag":"Unlimited",
      "tag_bg_color":"##535388",
      "tag_text_color":"##535388",
      "image": {
            "url": "https://cdn.waveapp.com/icons/birthday-coffee.png"
          },
      "title_text_color":"##FFFFFF",
    },
    {
      "title": "1 Free Coffee",
      "tag":"Claimed",
      "tag_bg_color":"##535388",
      "tag_text_color":"##535388",
      "image": {
            "url": "https://cdn.waveapp.com/icons/birthday-coffee.png"
          },
      "title_text_color":"##FFFFFF",
    }
    {
      "title": "1 Free Coffee",
      "tag": null,
      "tag_bg_color":"##535388",
      "tag_text_color":"##535388",
      "image": {
            "url": "https://cdn.waveapp.com/icons/birthday-coffee.png"
          },
      "title_text_color":"##FFFFFF",
    }
    ]
  }
}
```


## 6. Locked Loyalty Benefits

Returns current tier benefits and next tier benefits preview.

**URL:** `/api/v1/loyalty/locked-benefits`

**Method:** `GET`

### Response Body (Success) - Partner

```json
{
  "meta": {
    "request_id": "550e8400-e29b-41d4-a716-446655440011",
    "timestamp": "2026-01-21T14:32:00Z",
    "version": "1.0",
    "end_point": "/api/v1/loyalty/locked-benefits",
    "cacheable": false
  },
  "data": {
    "nextTierBenefits": [
    {
      "tier": "INFLUENCER",
      "title": "Unlock Influencer Benefits",
      "title_text_color":"##FFFFFF",
      "title_bg_color":["##71719C", "##535388"],
      "card_bg_color":["##AC6069", "##EC8893"],
      "card_border_color":"##56568A",
      "bg_color":"##FFFFFF",
      "benefits": [
        {
          "title": "Free coffee for your birthday",
          "image": {
            "url": "https://cdn.waveapp.com/icons/birthday-coffee.png"
          },
        },
        {
          "title": "Referral discount",
          "image": {
            "url": "https://cdn.waveapp.com/icons/referral.png"
          },
        },
        {
          "title": "10% of net payable bill amount",
          "image": {
            "url": "https://cdn.waveapp.com/icons/wave-coins.png"
          },
        },
        {
          "title": "1 free coffee",
          "image": {
            "url": "https://cdn.waveapp.com/icons/free-coffee.png"
          },
        }
      ]
    }
    {
      "tier": "AMBASSADOR",
      "title": "Unlock Ambassador Benefits",
      "title_text_color":"##FFFFFF",
      "title_bg_color":["##71719C", "##535388"],
      "card_bg_color":["##AC6069", "##EC8893"],
      "card_border_color":"##56568A",
      "bg_color":"##FFFFFF",
      "benefits": [
        {
          "title": "Free coffee for your birthday",
          "image": {
            "url": "https://cdn.waveapp.com/icons/birthday-coffee.png"
          },
        },
        {
          "title": "Referral discount",
          "image": {
            "url": "https://cdn.waveapp.com/icons/referral.png"
          },
        },
        {
          "title": "10% of net payable bill amount",
          "image": {
            "url": "https://cdn.waveapp.com/icons/wave-coins.png"
          },
        },
        {
          "title": "1 free coffee",
          "image": {
            "url": "https://cdn.waveapp.com/icons/free-coffee.png"
          },
        }
      ]
    }
    ]
  }
}
```

### Response Body (Success) - Influencer

```json
{
  "meta": {
    "request_id": "550e8400-e29b-41d4-a716-446655440011",
    "timestamp": "2026-01-21T14:32:00Z",
    "version": "1.0",
    "end_point": "/api/v1/loyalty/benefits",
    "cacheable": false
  },
  "data": {
    "nextTierBenefits": [
    {
      "tier": "AMBASSADOR",
      "title": "Unlock Ambassador Benefits",
      "title_text_color":"##FFFFFF",
      "title_bg_color":["##71719C", "##535388"],
      "card_bg_color":["##AC6069", "##EC8893"],
      "card_border_color":"##56568A",
      "bg_color":"##FFFFFF",
      "benefits": [
        {
          "title": "Free coffee for your birthday",
          "image": {
            "url": "https://cdn.waveapp.com/icons/birthday-coffee.png"
          },
        },
        {
          "title": "Referral discount",
          "image": {
            "url": "https://cdn.waveapp.com/icons/referral.png"
          },
        },
        {
          "title": "10% of net payable bill amount",
          "image": {
            "url": "https://cdn.waveapp.com/icons/wave-coins.png"
          },
        },
        {
          "title": "1 free coffee",
          "image": {
            "url": "https://cdn.waveapp.com/icons/free-coffee.png"
          },
        }
      ]
    }
    ]
  }
}
```

---

## 6. Loyalty FAQ

Returns FAQ items for the loyalty program.

**URL:** `/api/v2/loyalty/faq/`

**Method:** `GET`

### Response Body (Success)

```json
{
  "meta": {
    "request_id": "550e8400-e29b-41d4-a716-446655440014",
    "timestamp": "2026-01-21T14:32:00Z",
    "version": "1.0",
    "end_point": "/api/v2/faq/loyalty",
    "cacheable": true
  },
  "data": {
    "title": "FAQs",
    "faqs": [
      {
        "question": "How do I become a Partner?",
        "answer": "You automatically become a Partner when you register on the Wave app. As a Partner, you can start placing orders and progress towards higher tiers."
      },
      {
        "question": "How do I advance to Influencer?",
        "answer": "Place 6 orders within a 90-day cycle to become an Influencer. You'll unlock benefits like 10% Wave Coins on every order and a free birthday coffee."
      },
      {
        "question": "How do I advance to Ambassador?",
        "answer": "Place 12 orders within a 90-day cycle to become an Ambassador. You'll enjoy 15% Wave Coins, 2 free coffees on upgrade, and exclusive birthday benefits."
      },
      {
        "question": "What happens if I don't maintain my tier?",
        "answer": "If you don't place the required orders within your 90-day cycle, you'll be moved to the previous tier. Influencers need 6 orders to maintain, Ambassadors need 12."
      },
      {
        "question": "How long are Wave Coins valid?",
        "answer": "Wave Coins are valid for 1 year from the date they are earned. Use them before they expire!"
      }
    ],
  }
}
```

---


## 7. Loyalty Progress Widget for App Scan Bottom Sheet

![alt text](image.png)

**URL:** `/api/v1/loyalty/progress-widget`

**Method:** `GET`

### Response Body - Partner (progressing to Influencer)

```json
{
  "meta": {
    "request_id": "550e8400-e29b-41d4-a716-446655440001",
    "timestamp": "2026-01-21T14:32:00Z",
    "version": "1.0",
    "end_point": "/api/v1/loyalty/progress-widget",
    "cacheable": false
  },
  "data": {
    "currentTier": {
      "tier": "PARTNER",
      "displayLabel": "Partner",
      "image": {
        "url": "https://cdn.waveapp.com/avatars/partner.png"
      },
    },
    "nextTier": {
      "tier": "INFLUENCER",
      "displayLabel": "Influencer",
      "image": {
        "url": "https://cdn.waveapp.com/avatars/partner.png"
      },
    },
    "progress": {
      "message": "Just 3 more orders to unlock your next level!",
      "style": {
        "progress_color": "#4db436",
        "track_color": "#656060"
      },
      "ordersCompleted": 3,
      "ordersRequired": 6,
    }
  }
}
```

### Response Body - Influencer (progressing to Ambassador)

```json
{
  "meta": {
    "request_id": "550e8400-e29b-41d4-a716-446655440002",
    "timestamp": "2026-01-21T14:32:00Z",
    "version": "1.0",
    "end_point": "/api/v1/loyalty/progress-widget",
    "cacheable": false
  },
  "data": {
    "currentTier": {
      "tier": "INFLUENCER",
      "displayLabel": "Influencer",
      "image": {
        "url": "https://cdn.waveapp.com/avatars/partner.png"
      },
    },
    "nextTier": {
      "tier": "AMBASSADOR",
      "displayLabel": "Ambassador",
      "image": {
        "url": "https://cdn.waveapp.com/avatars/partner.png"
      },
    },
    "progress": {
      "message": "Just 3 more orders to unlock your next level!",
      "style": {
        "progress_color": "#4db436",
        "track_color": "#656060"
      },
      "ordersCompleted": 3,
      "ordersRequired": 6,
    }
  }
}
```

### Response Body - Ambassador


```json
{
  "meta": {
    "request_id": "550e8400-e29b-41d4-a716-446655440003",
    "timestamp": "2026-01-21T14:32:00Z",
    "version": "1.0",
    "end_point": "/api/v1/loyalty/progress-widget",
    "cacheable": false
  },
  "data": {
    "currentTier": {
      "tier": "AMBASSADOR",
      "displayLabel": "Ambassador",
      "image": {
        "url": "https://cdn.waveapp.com/avatars/partner.png"
      },
    },
    "nextTier": null,
    "progress": {
      "message": "9 more orders to retain your Ambassador status",
      "style": {
        "progress_color": "#4db436",
        "track_color": "#656060"
      },
      "ordersCompleted": 6,
      "ordersRequired": 12,
    },
  }
}
```
