# Loyalty Page Contracts

## APIs
- [Loyalty Skeleton](#loyalty-skeleton)

## Loyalty Skeleton


URL : `/api/v1/loyalty/skeleton`


Method: `GET`

Response Body (Success)
```json
{
  "meta": {
    "request_id": "req-loyalty-123",
    "timestamp": "2026-01-20T16:15:00Z",
    "version": "1.0",
    "end_point": "/api/v1/loyalty/skeleton"
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
        "widget_name": "tier_progress_bar", 
        "view_type": "progress_indicator" 
        },
      {
        "widget_name": "tier_benefits", 
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