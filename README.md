# Loyalty Page Contracts

## APIs
- [Loyalty Skeleton](#loyalty-skeleton)


## Tier
```json
Partner
Influencer
Ambassador
```


## Loyalty Page - Partner (with Brew Journey)

URL : `/api/v1/loyalty/status`

Method: `GET`

Response Body (Success)
```json
{
  "meta": {
    "request_id": "550e8400-e29b-41d4-a716-446655440000",
    "timestamp": "2024-03-21T14:32:00Z",
    "version": "1.0",
    "end_point": "/api/v1/loyalty/status",
    "cacheable": false
  },
  "success": true,
  "data": {
    "user": {
      "id": "usr_partner_001",
      "displayName": "John",
      "avatarUrl": "https://cdn.waveapp.com/avatars/default.png"
    },
    "tier": {
      "current": "PARTNER",
      "displayName": "Partner",
      "level": 1,
      "colorHex": "#DC3545",
      "backgroundColorHex": "#8B4A5E"
    },
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
        "colorHex": "#20B2AA"
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
    "migration": null,
    "brewJourney": {
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
          "iconUrl": "https://cdn.waveapp.com/icons/discount-100.png",
          "status": "UNLOCKED",
          "value": "₹100 Off"
        },
        {
          "step": 2,
          "type": "FREE_COFFEE",
          "title": "Free Coffee",
          "iconUrl": "https://cdn.waveapp.com/icons/free-coffee.png",
          "status": "LOCKED",
          "value": null
        },
        {
          "step": 3,
          "type": "DISCOUNT_PERCENTAGE",
          "title": "15% Off",
          "iconUrl": "https://cdn.waveapp.com/icons/discount-15.png",
          "status": "LOCKED",
          "value": "15%"
        },
        {
          "step": 4,
          "type": "COUPON",
          "title": "Special Coupon",
          "iconUrl": "https://cdn.waveapp.com/icons/coupon.png",
          "status": "LOCKED",
          "value": null
        },
        {
          "step": 5,
          "type": "FREE_COFFEE",
          "title": "Free Coffee",
          "iconUrl": "https://cdn.waveapp.com/icons/trophy.png",
          "status": "LOCKED",
          "value": null
        }
      ],
      "ctaText": "Know more",
      "title": "Start your Brew Journey - Complete 5 orders",
      "subtitle": "in 45 days to unlock exclusive rewards",
      "urgencyMessage": "Hurry!! 5 days remaining to use the sign up offer"
    },
    "benefits": {
      "currentTierBenefits": null,
      "nextTierBenefits": {
        "tier": "INFLUENCER",
        "title": "Unlock Influencer Benefits",
        "subtitle": null,
        "isUnlocked": false,
        "benefits": [
          {
            "id": "benefit_birthday_inf",
            "type": "BIRTHDAY_OFFER",
            "title": "Free coffee for your birthday",
            "description": null,
            "iconUrl": "https://cdn.waveapp.com/icons/birthday-coffee.png",
            "isActive": false,
            "displayValue": null,
            "metadata": {}
          },
          {
            "id": "benefit_referral_inf",
            "type": "REFERRAL_DISCOUNT",
            "title": "Referral discount",
            "description": null,
            "iconUrl": "https://cdn.waveapp.com/icons/referral.png",
            "isActive": false,
            "displayValue": null,
            "metadata": {}
          },
          {
            "id": "benefit_coins_inf",
            "type": "WAVE_COINS",
            "title": "10% of net payable bill amount",
            "description": null,
            "iconUrl": "https://cdn.waveapp.com/icons/wave-coins.png",
            "isActive": false,
            "displayValue": "10%",
            "metadata": {
              "earnPercentage": 10
            }
          },
          {
            "id": "benefit_coffee_inf",
            "type": "FREE_COFFEE",
            "title": "1 free coffee",
            "description": null,
            "iconUrl": "https://cdn.waveapp.com/icons/free-coffee.png",
            "isActive": false,
            "displayValue": "1 Free Coffee",
            "metadata": {
              "coffeeCount": 1
            }
          }
        ]
      }
    }
  }
}
```



## Loyalty Page - Ambassador

URL : `/api/v1/loyalty/status`

Method: `GET`

Response Body (Success)
```json
{
  "meta": {
    "request_id": "550e8400-e29b-41d4-a716-446655440000",
    "timestamp": "2024-03-21T14:32:00Z",
    "version": "1.0",
    "end_point": "/api/v1/loyalty/status",
    "cacheable": false
  },
  "success": true,
  "data": {
    "user": {
      "id": "usr_ambassador_001",
      "displayName": "Mike",
      "avatarUrl": "https://cdn.waveapp.com/avatars/mike.png"
    },
    "tier": {
      "current": "AMBASSADOR",
      "displayName": "Ambassador",
      "level": 3,
      "colorHex": "#4A5D23",
      "backgroundColorHex": "#3D4A2A"
    },
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
    "migration": null,
    "brewJourney": null,
    "benefits": {
      "currentTierBenefits": {
        "tier": "AMBASSADOR",
        "title": "Ambassador Benefits",
        "subtitle": "Your exclusive perks as an Ambassador",
        "isUnlocked": true,
        "benefits": [
          {
            "id": "benefit_referral_amb_active",
            "type": "REFERRAL_DISCOUNT",
            "title": "Referral Discount",
            "description": null,
            "iconUrl": "https://cdn.waveapp.com/icons/referral-gold.png",
            "isActive": true,
            "displayValue": null,
            "metadata": {}
          },
          {
            "id": "benefit_coffee_amb_active",
            "type": "FREE_COFFEE",
            "title": "2 Free Coffees",
            "description": "on level upgrade",
            "iconUrl": "https://cdn.waveapp.com/icons/free-coffee-gold.png",
            "isActive": true,
            "displayValue": "Earned",
            "metadata": {
              "coffeeCount": 2
            }
          },
          {
            "id": "benefit_birthday_amb_active",
            "type": "BIRTHDAY_OFFER",
            "title": "Birthday Coffee",
            "description": null,
            "iconUrl": "https://cdn.waveapp.com/icons/birthday-gold.png",
            "isActive": true,
            "displayValue": null,
            "metadata": {}
          }
        ]
      },
      "nextTierBenefits": null
    }
  }
}
```

## Loyalty Page - Migration State

URL : `/api/v1/loyalty/status`

Method: `GET`

Response Body (Success)
```json
{
  "meta": {
    "request_id": "550e8400-e29b-41d4-a716-446655440000",
    "timestamp": "2024-03-21T14:32:00Z",
    "version": "1.0",
    "end_point": "/api/v1/loyalty/status",
    "cacheable": false
  },
  "success": true,
  "data": {
    "user": {
      "id": "usr_migrated_001",
      "displayName": "Anna",
      "avatarUrl": "https://cdn.waveapp.com/avatars/anna.png"
    },
    "tier": {
      "current": "AMBASSADOR",
      "displayName": "Ambassador",
      "level": 3,
      "colorHex": "#4A5D23",
      "backgroundColorHex": "#3D4A2A"
    },
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
    },
    "brewJourney": null,
    "benefits": {
      "currentTierBenefits": {
        "tier": "AMBASSADOR",
        "title": "Ambassador Benefits",
        "subtitle": "Your exclusive perks as an Ambassador",
        "isUnlocked": true,
        "benefits": [
          {
            "id": "benefit_referral_amb_active",
            "type": "REFERRAL_DISCOUNT",
            "title": "Referral Discount",
            "description": null,
            "iconUrl": "https://cdn.waveapp.com/icons/referral-gold.png",
            "isActive": true,
            "displayValue": null,
            "metadata": {}
          },
          {
            "id": "benefit_coffee_amb_active",
            "type": "FREE_COFFEE",
            "title": "2 Free Coffees",
            "description": "on level upgrade",
            "iconUrl": "https://cdn.waveapp.com/icons/free-coffee-gold.png",
            "isActive": true,
            "displayValue": "Earned",
            "metadata": {
              "coffeeCount": 2
            }
          },
          {
            "id": "benefit_birthday_amb_active",
            "type": "BIRTHDAY_OFFER",
            "title": "Birthday Coffee",
            "description": null,
            "iconUrl": "https://cdn.waveapp.com/icons/birthday-gold.png",
            "isActive": true,
            "displayValue": null,
            "metadata": {}
          }
        ]
      },
      "nextTierBenefits": null
    }
  }
}
```

## Loyalty FAQ

URL : `/api/v2/faq/loyalty`

Method: `GET`

Response Body (Success)
```json
{
  "meta": {
    "request_id": "550e8400-e29b-41d4-a716-446655440000",
    "timestamp": "2024-03-21T14:32:00Z",
    "version": "1.0",
    "end_point": "/api/v2/faq/loyalty",
    "cacheable": false
  },
  "data": {
    "faqs": [
        {
            "question": "How do I become a Partner?",
            "answer": "Lorem ipsum dolor sit amet Lorem ipsum dolor sit amet lore Lorem ipsum dolor sit amet Lorem ipsum dolor sit amet Lorem ipsum dolor sit amet Lorem ipsum dolor sit amet"
        },
        {
            "question": "How do I advance to Influencer?",
            "answer": "Lorem ipsum dolor sit amet Lorem ipsum dolor sit amet lore Lorem ipsum dolor sit amet Lorem ipsum dolor sit amet Lorem ipsum dolor sit amet Lorem ipsum dolor sit amet"
        },
        {
            "question": "How do I advance to Ambassador?",
            "answer": "Lorem ipsum dolor sit amet Lorem ipsum dolor sit amet lore Lorem ipsum dolor sit amet Lorem ipsum dolor sit amet Lorem ipsum dolor sit amet Lorem ipsum dolor sit amet"
        }
    ]
  },
  "meta": {
    "request_id": "550e8400-e29b-41d4-a716-446655440000",
    "timestamp": "2024-03-21T14:32:00Z",
    "version": "1.0",
    "end_point": "/api/v2/faq/loyalty",
    "cacheable": false
  }
}
```

