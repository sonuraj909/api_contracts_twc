# Loyalty Page API Contracts 

---

## APIs

- [Loyalty Skeleton](#1-loyalty-skeleton)
- [Loyalty Header](#2-loyalty-header)
- [Loyalty Progression](#3-loyalty-progression)
- [Loyalty Brew Journey](#4-loyalty-brew-journey)
- [Loyalty Benefits](#5-loyalty-benefits)
- [Loyalty FAQ](#6-loyalty-faq)

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
        "url": "https://cdn.waveapp.com/avatars/default.png"
      },
      "bg_color": ["##AC6069", "##EC8893"]
    },
    "progression": {
      "currentOrderCount": 4,
      "progressMessage": "2 orders away from becoming an Influencer",
      "progressPercentage": 66.67,
      "milestones": [
        {
          "tier": "PARTNER",
          "orderThreshold": 0,
          "displayLabel": "Partner",
          "status": "CURRENT",
          "orderCountDisplay": "3 orders / 37 days"
        },
        {
          "tier": "INFLUENCER",
          "orderThreshold": 6,
          "displayLabel": "Influencer",
          "status": "LOCKED",
          "orderCountDisplay": "0/6"
        },
        {
          "tier": "AMBASSADOR",
          "orderThreshold": 12,
          "displayLabel": "Ambassador",
          "status": "LOCKED",
          "orderCountDisplay": "0/6"
        }
      ]
    },
    "cycle": {
      "startDate": "2025-12-15T00:00:00Z",
      "endDate": "2026-03-15T00:00:00Z",
      "daysRemaining": 53,
      "totalDays": 90,
      "maintenanceMessage": "Make 15 Orders by 9 March, to maintain this level.",
      "ordersForMaintenance": 6,
      "currentCycleOrders": 4,
      "isMigrationCycle": false
    },
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
    "user": {
      "id": "usr_b2c3d4e5f6g7",
      "displayName": "Sarah",
      "image": {
        "url": "https://cdn.waveapp.com/avatars/sarah.png"
      }
    },
    "tier": {
      "current": "INFLUENCER",
      "displayName": "Influencer",
      "level": 2,
      "bg_color": ["#5FA09E", "#9FDCD8"]
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
    "user": {
      "id": "usr_c3d4e5f6g7h8",
      "displayName": "Mike",
      "image": {
        "url": "https://cdn.waveapp.com/avatars/mike.png"
      }
    },
    "tier": {
      "current": "AMBASSADOR",
      "displayName": "Ambassador",
      "level": 3,
      "bg_color": ["#6B8A3D", "#A8C973"]
    }
  }
}
```

---

## 3. Loyalty Progression

Returns tier progression, milestones, and cycle information.

**URL:** `/api/v1/loyalty/progression`

**Method:** `GET`

### Response Body (Success) - Partner (4 orders)

```json
{
  "meta": {
    "request_id": "550e8400-e29b-41d4-a716-446655440004",
    "timestamp": "2026-01-21T14:32:00Z",
    "version": "1.0",
    "end_point": "/api/v1/loyalty/progression",
    "cacheable": false
  },
  "data": {
    "progression": {
      "currentOrderCount": 4,
      "ordersToNextTier": 2,
      "progressMessage": "2 orders away from becoming an Influencer",
      "progressPercentage": 66.67,
      "nextTier": {
        "name": "INFLUENCER",
        "displayName": "Influencer",
        "level": 2,
        "requiredOrders": 6,
        "bg_color": ["#5FA09E", "#9FDCD8"]
      },
      "milestones": [
        {
          "tier": "PARTNER",
          "orderThreshold": 0,
          "displayLabel": "Partner",
          "status": "CURRENT",
          "orderCountDisplay": "3 orders / 37 days"
        },
        {
          "tier": "INFLUENCER",
          "orderThreshold": 6,
          "displayLabel": "Influencer",
          "status": "LOCKED",
          "orderCountDisplay": "0/6"
        },
        {
          "tier": "AMBASSADOR",
          "orderThreshold": 12,
          "displayLabel": "Ambassador",
          "status": "LOCKED",
          "orderCountDisplay": "0/6"
        }
      ]
    },
    "cycle": {
      "startDate": "2025-12-15T00:00:00Z",
      "endDate": "2026-03-15T00:00:00Z",
      "daysRemaining": 53,
      "totalDays": 90,
      "maintenanceMessage": "Make 15 Orders by 9 March, to maintain this level.",
      "ordersForMaintenance": 6,
      "currentCycleOrders": 4,
      "isMigrationCycle": false
    },
    "migration": null
  }
}
```

### Response Body (Success) - Influencer (7 orders)

```json
{
  "meta": {
    "request_id": "550e8400-e29b-41d4-a716-446655440005",
    "timestamp": "2026-01-21T14:32:00Z",
    "version": "1.0",
    "end_point": "/api/v1/loyalty/progression",
    "cacheable": false
  },
  "data": {
    "progression": {
      "currentOrderCount": 7,
      "ordersToNextTier": 5,
      "progressMessage": "5 orders away from becoming an Ambassador",
      "progressPercentage": 58.33,
      "nextTier": {
        "name": "AMBASSADOR",
        "displayName": "Ambassador",
        "level": 3,
        "requiredOrders": 12,
        "bg_color": ["#6B8A3D", "#A8C973"]
      },
      "milestones": [
        {
          "tier": "PARTNER",
          "orderThreshold": 0,
          "displayLabel": "Partner",
          "status": "COMPLETED",
          "orderCountDisplay": "Completed"
        },
        {
          "tier": "INFLUENCER",
          "orderThreshold": 6,
          "displayLabel": "Influencer",
          "status": "CURRENT",
          "orderCountDisplay": "5 orders / 24 days"
        },
        {
          "tier": "AMBASSADOR",
          "orderThreshold": 12,
          "displayLabel": "Ambassador",
          "status": "LOCKED",
          "orderCountDisplay": "0/6"
        }
      ]
    },
    "cycle": {
      "startDate": "2025-12-28T00:00:00Z",
      "endDate": "2026-03-28T00:00:00Z",
      "daysRemaining": 66,
      "totalDays": 90,
      "maintenanceMessage": "Make 15 Orders by 9 March, to maintain this level.",
      "ordersForMaintenance": 6,
      "currentCycleOrders": 7,
      "isMigrationCycle": false
    },
    "migration": null
  }
}
```

### Response Body (Success) - Ambassador (15 orders)

```json
{
  "meta": {
    "request_id": "550e8400-e29b-41d4-a716-446655440006",
    "timestamp": "2026-01-21T14:32:00Z",
    "version": "1.0",
    "end_point": "/api/v1/loyalty/progression",
    "cacheable": false
  },
  "data": {
    "progression": {
      "currentOrderCount": 15,
      "ordersToNextTier": null,
      "progressMessage": "You've reached the highest tier!",
      "progressPercentage": 100,
      "nextTier": null,
      "milestones": [
        {
          "tier": "PARTNER",
          "orderThreshold": 0,
          "displayLabel": "Partner",
          "status": "COMPLETED",
          "orderCountDisplay": "Completed"
        },
        {
          "tier": "INFLUENCER",
          "orderThreshold": 6,
          "displayLabel": "Influencer",
          "status": "COMPLETED",
          "orderCountDisplay": "Completed"
        },
        {
          "tier": "AMBASSADOR",
          "orderThreshold": 12,
          "displayLabel": "Ambassador",
          "status": "CURRENT",
          "orderCountDisplay": "12+ orders / 90 days"
        }
      ]
    },
    "cycle": {
      "startDate": "2025-11-15T00:00:00Z",
      "endDate": "2026-02-13T00:00:00Z",
      "daysRemaining": 23,
      "totalDays": 90,
      "maintenanceMessage": "Make 15 Orders by 9 March, to maintain this level.",
      "ordersForMaintenance": 12,
      "currentCycleOrders": 15,
      "isMigrationCycle": false
    },
    "migration": null
  }
}
```

### Response Body (Success) - Migration State

```json
{
  "meta": {
    "request_id": "550e8400-e29b-41d4-a716-446655440007",
    "timestamp": "2026-01-21T14:32:00Z",
    "version": "1.0",
    "end_point": "/api/v1/loyalty/progression",
    "cacheable": false
  },
  "data": {
    "progression": {
      "currentOrderCount": 12,
      "ordersToNextTier": null,
      "progressMessage": "You've reached the highest tier!",
      "progressPercentage": 100,
      "nextTier": null,
      "milestones": [
        {
          "tier": "PARTNER",
          "orderThreshold": 0,
          "displayLabel": "Partner",
          "status": "COMPLETED",
          "orderCountDisplay": "Completed"
        },
        {
          "tier": "INFLUENCER",
          "orderThreshold": 6,
          "displayLabel": "Influencer",
          "status": "COMPLETED",
          "orderCountDisplay": "Completed"
        },
        {
          "tier": "AMBASSADOR",
          "orderThreshold": 12,
          "displayLabel": "Ambassador",
          "status": "CURRENT",
          "orderCountDisplay": "12 orders / 90 days"
        }
      ]
    },
    "cycle": {
      "startDate": "2025-08-01T00:00:00Z",
      "endDate": "2026-01-28T00:00:00Z",
      "daysRemaining": 7,
      "totalDays": 180,
      "maintenanceMessage": "Make 15 Orders by 9 March, to maintain this level.",
      "ordersForMaintenance": 12,
      "currentCycleOrders": 12,
      "isMigrationCycle": true
    },
    "migration": {
      "isMigrated": true,
      "migrationDate": "2026-01-15T00:00:00Z",
      "legacyCycleDaysRemaining": 7,
      "originalTier": "AMBASSADOR",
      "migratedOrderCount": 12,
      "specialMessage": "More 12 orders within this 90-day cycle"
    }
  }
}
```

---

## 4. Loyalty Brew Journey

Returns Brew Journey status. Returns `null` data if user is not in Brew Journey.

**URL:** `/api/v1/loyalty/brew-journey`

**Method:** `GET`

### Response Body (Success) - Active Brew Journey (New User)

```json
{
  "meta": {
    "request_id": "550e8400-e29b-41d4-a716-446655440008",
    "timestamp": "2026-01-21T14:32:00Z",
    "version": "1.0",
    "end_point": "/api/v1/loyalty/brew-journey",
    "cacheable": false
  },
  "data": {
    "isActive": true,
    "journeyType": "NEW",
    "totalSteps": 5,
    "currentStep": 1,
    "completedOrders": 1,
    "daysRemaining": 40,
    "totalDays": 45,
    "movRequirement": 300,
    "signUpOfferDaysRemaining": 5,
    "rewards": [
      {
        "step": 1,
        "type": "DISCOUNT_FLAT",
        "title": "₹100 Off",
        "image": {
          "url": "https://cdn.waveapp.com/icons/discount-100.png"
        },
        "status": "UNLOCKED",
        "value": "₹100 Off"
      },
      {
        "step": 2,
        "type": "FREE_COFFEE",
        "title": "Free Coffee",
        "image": {
          "url": "https://cdn.waveapp.com/icons/free-coffee.png"
        },
        "status": "LOCKED",
        "value": null
      },
      {
        "step": 3,
        "type": "DISCOUNT_PERCENTAGE",
        "title": "15% Off",
        "image": {
          "url": "https://cdn.waveapp.com/icons/discount-15.png"
        },
        "status": "LOCKED",
        "value": "15%"
      },
      {
        "step": 4,
        "type": "COUPON",
        "title": "Special Coupon",
        "image": {
          "url": "https://cdn.waveapp.com/icons/coupon.png"
        },
        "status": "LOCKED",
        "value": null
      },
      {
        "step": 5,
        "type": "FREE_COFFEE",
        "title": "Free Coffee",
        "image": {
          "url": "https://cdn.waveapp.com/icons/trophy.png"
        },
        "status": "LOCKED",
        "value": null
      }
    ],
    "ctaText": "Know more",
    "title": "Start your Brew Journey - Complete 5 orders",
    "subtitle": "in 45 days to unlock exclusive rewards",
    "urgencyMessage": "Hurry!! 5 days remaining to use the sign up offer"
  }
}
```

### Response Body (Success) - Migrated Brew Journey (Old User)

```json
{
  "meta": {
    "request_id": "550e8400-e29b-41d4-a716-446655440009",
    "timestamp": "2026-01-21T14:32:00Z",
    "version": "1.0",
    "end_point": "/api/v1/loyalty/brew-journey",
    "cacheable": false
  },
  "data": {
    "isActive": true,
    "journeyType": "OLD",
    "totalSteps": 5,
    "currentStep": 3,
    "completedOrders": 3,
    "daysRemaining": 20,
    "totalDays": 45,
    "movRequirement": 400,
    "signUpOfferDaysRemaining": 0,
    "rewards": [
      {
        "step": 1,
        "type": "DISCOUNT_FLAT",
        "title": "₹100 Off",
        "image": {
          "url": "https://cdn.waveapp.com/icons/discount-100.png"
        },
        "status": "REDEEMED",
        "value": "₹100 Off"
      },
      {
        "step": 2,
        "type": "DISCOUNT_PERCENTAGE",
        "title": "15% Off",
        "image": {
          "url": "https://cdn.waveapp.com/icons/discount-15.png"
        },
        "status": "UNLOCKED",
        "value": "15%"
      },
      {
        "step": 3,
        "type": "COUPON",
        "title": "Special Coupon",
        "image": {
          "url": "https://cdn.waveapp.com/icons/coupon.png"
        },
        "status": "LOCKED",
        "value": null
      },
      {
        "step": 4,
        "type": "COUPON",
        "title": "Special Coupon",
        "image": {
          "url": "https://cdn.waveapp.com/icons/coupon.png"
        },
        "status": "LOCKED",
        "value": null
      },
      {
        "step": 5,
        "type": "FREE_COFFEE",
        "title": "Free Coffee",
        "image": {
          "url": "https://cdn.waveapp.com/icons/trophy.png"
        },
        "status": "LOCKED",
        "value": null
      }
    ],
    "ctaText": "Know more",
    "title": "Continue your Brew Journey - 2 orders to go",
    "subtitle": "Complete within 20 days to unlock rewards",
    "urgencyMessage": null
  }
}
```

### Response Body (Success) - No Brew Journey

```json
{
  "meta": {
    "request_id": "550e8400-e29b-41d4-a716-446655440010",
    "timestamp": "2026-01-21T14:32:00Z",
    "version": "1.0",
    "end_point": "/api/v1/loyalty/brew-journey",
    "cacheable": false
  },
  "data": null
}
```

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

**URL:** `/api/v2/faq/loyalty`

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

## 7. Error Response

All APIs return errors in the following format:

```json
{
  "meta": {
    "request_id": "550e8400-e29b-41d4-a716-446655440099",
    "timestamp": "2026-01-21T14:32:00Z",
    "version": "1.0",
    "end_point": "/api/v1/loyalty/header",
    "cacheable": false
  },
  "error": {
    "code": "UNAUTHORIZED",
    "message": "Invalid or expired authentication token",
    "details": null
  }
}
```

### Error Codes

| HTTP Status | Code | Description |
|-------------|------|-------------|
| 400 | `BAD_REQUEST` | Invalid request parameters |
| 401 | `UNAUTHORIZED` | Invalid/expired authentication token |
| 403 | `FORBIDDEN` | Access denied to resource |
| 404 | `NOT_FOUND` | Resource not found |
| 429 | `RATE_LIMITED` | Too many requests |
| 500 | `INTERNAL_ERROR` | Server error |
| 503 | `SERVICE_UNAVAILABLE` | Service temporarily unavailable |

---

## 8. Data Models (TypeScript)

```typescript
// ============================================
// ENUMS
// ============================================

type TierType = "PARTNER" | "INFLUENCER" | "AMBASSADOR";
type MilestoneStatus = "COMPLETED" | "CURRENT" | "LOCKED";
type BrewJourneyType = "OLD" | "NEW";
type RewardType = "DISCOUNT_PERCENTAGE" | "DISCOUNT_FLAT" | "FREE_COFFEE" | "COUPON";
type RewardStatus = "LOCKED" | "UNLOCKED" | "REDEEMED";
type BenefitType = "WAVE_COINS" | "BIRTHDAY_OFFER" | "FREE_COFFEE" | "REFERRAL_DISCOUNT";

// ============================================
// META
// ============================================

interface ResponseMeta {
  request_id: string;
  timestamp: string;
  version: string;
  end_point: string;
  cacheable: boolean;
}

// ============================================
// IMAGE
// ============================================

interface Image {
  url: string;
}

// ============================================
// SKELETON
// ============================================

interface SkeletonResponse {
  meta: ResponseMeta;
  data: {
    skeleton: WidgetSkeleton[];
  };
}

interface WidgetSkeleton {
  widget_name: string;
  view_type: string;
}

// ============================================
// HEADER
// ============================================

interface HeaderResponse {
  meta: ResponseMeta;
  data: HeaderData;
}

interface HeaderData {
  user: UserProfile;
  tier: TierInfo;
}

interface UserProfile {
  id: string;
  displayName: string;
  image: Image;
}

interface TierInfo {
  current: TierType;
  displayName: string;
  level: number;
  bg_color: [string, string];
}

// ============================================
// PROGRESSION
// ============================================

interface ProgressionResponse {
  meta: ResponseMeta;
  data: ProgressionData;
}

interface ProgressionData {
  progression: TierProgression;
  cycle: CycleInfo;
  migration: MigrationInfo | null;
}

interface TierProgression {
  currentOrderCount: number;
  ordersToNextTier: number | null;
  progressMessage: string;
  progressPercentage: number;
  nextTier: NextTierInfo | null;
  milestones: TierMilestone[];
}

interface NextTierInfo {
  name: TierType;
  displayName: string;
  level: number;
  requiredOrders: number;
  bg_color: [string, string];
}

interface TierMilestone {
  tier: TierType;
  orderThreshold: number;
  displayLabel: string;
  status: MilestoneStatus;
  orderCountDisplay: string;
}

interface CycleInfo {
  startDate: string;
  endDate: string;
  daysRemaining: number;
  totalDays: number;
  maintenanceMessage: string;
  ordersForMaintenance: number;
  currentCycleOrders: number;
  isMigrationCycle: boolean;
}

interface MigrationInfo {
  isMigrated: boolean;
  migrationDate: string;
  legacyCycleDaysRemaining: number;
  originalTier: TierType;
  migratedOrderCount: number;
  specialMessage: string | null;
}

// ============================================
// BREW JOURNEY
// ============================================

interface BrewJourneyResponse {
  meta: ResponseMeta;
  data: BrewJourneyData | null;
}

interface BrewJourneyData {
  isActive: boolean;
  journeyType: BrewJourneyType;
  totalSteps: number;
  currentStep: number;
  completedOrders: number;
  daysRemaining: number;
  totalDays: number;
  movRequirement: number;
  signUpOfferDaysRemaining: number;
  rewards: BrewJourneyReward[];
  ctaText: string;
  title: string;
  subtitle: string;
  urgencyMessage: string | null;
}

interface BrewJourneyReward {
  step: number;
  type: RewardType;
  title: string;
  image: Image;
  status: RewardStatus;
  value: string | null;
}

// ============================================
// BENEFITS
// ============================================

interface BenefitsResponse {
  meta: ResponseMeta;
  data: BenefitsData;
}

interface BenefitsData {
  currentTierBenefits: TierBenefitCard | null;
  nextTierBenefits: TierBenefitCard | null;
}

interface TierBenefitCard {
  tier: TierType;
  title: string;
  subtitle: string | null;
  isUnlocked: boolean;
  benefits: BenefitItem[];
}

interface BenefitItem {
  id: string;
  type: BenefitType;
  title: string;
  description: string | null;
  image: Image;
  isActive: boolean;
  displayValue: string | null;
  metadata: Record<string, any>;
}

// ============================================
// FAQ
// ============================================

interface FAQResponse {
  meta: ResponseMeta;
  data: FAQData;
}

interface FAQData {
  title: string;
  faqs: FAQItem[];
  support: SupportInfo;
}

interface FAQItem {
  id: string;
  question: string;
  answer: string;
}

interface SupportInfo {
  showChatSupport: boolean;
  chatSupportCta: string | null;
  chatSupportUrl: string | null;
}

// ============================================
// ERROR
// ============================================

interface ErrorResponse {
  meta: ResponseMeta;
  error: {
    code: string;
    message: string;
    details: Record<string, any> | null;
  };
}
```

---

## 9. API Endpoints Summary

| # | Endpoint | Description | Cache TTL |
|---|----------|-------------|-----------|
| 1 | `GET /api/v1/loyalty/skeleton` | Widget skeleton config | 24 hours |
| 2 | `GET /api/v1/loyalty/header` | User profile + Tier info | 5 min |
| 3 | `GET /api/v1/loyalty/progression` | Tier progression + Cycle info | 5 min |
| 4 | `GET /api/v1/loyalty/brew-journey` | Brew Journey status | 1 min |
| 5 | `GET /api/v1/loyalty/benefits` | Current & Next tier benefits | 1 hour |
| 6 | `GET /api/v2/faq/loyalty` | FAQ items + Support info | 24 hours |

---

## 10. Widget to API Mapping

| Widget Name | View Type | API Endpoint |
|-------------|-----------|--------------|
| `loyalty_header` | `header_card` | `/api/v1/loyalty/header` |
| `tier_progress_bar` | `progress_indicator` | `/api/v1/loyalty/progression` |
| `brew_journey_status` | `stepper_card` | `/api/v1/loyalty/brew-journey` |
| `tier_benefits` | `grid_layout` | `/api/v1/loyalty/benefits` |
| `loyalty_faqs` | `accordion_list` | `/api/v2/faq/loyalty` |

---

## 11. Frontend Loading Strategy

### Recommended Loading Order

```
1. Skeleton API       → Render skeleton immediately
2. Header API         → Load first (critical for page header)
3. Progression API    → Load second (progress bar)
4. Brew Journey API   → Load third (if applicable)
5. Benefits API       → Load fourth
6. FAQs API           → Load last (least critical)
```

### Parallel Loading Example

```typescript
async function loadLoyaltyPage() {
  // Load skeleton first for immediate UI
  const skeleton = await fetch('/api/v1/loyalty/skeleton');
  renderSkeleton(skeleton);
  
  // Load all data APIs in parallel
  const [header, progression, brewJourney, benefits, faqs] = await Promise.all([
    fetch('/api/v1/loyalty/header'),
    fetch('/api/v1/loyalty/progression'),
    fetch('/api/v1/loyalty/brew-journey'),
    fetch('/api/v1/loyalty/benefits'),
    fetch('/api/v2/faq/loyalty')
  ]);
  
  // Render each section as data arrives
  renderHeader(header);
  renderProgression(progression);
  renderBrewJourney(brewJourney);
  renderBenefits(benefits);
  renderFAQs(faqs);
}
```

---

**End of Document**
