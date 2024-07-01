# DSEP JSON Structure Documentation

## The 3 major types of interactions
1. The user interactions
2. The system processes
3. The seller/vendor responses

## The breakdown of the user interaction flow:
- Discovery of a product/service
- Consumption of a product/service
- Accessing support
- Providing rating and submitting feedback

## Detailed Breakdown:
- Discovery of a product/service:
    - User's search request JSON
    - System's search results JSON

- Consumption of a product/service:
    - User's content selection JSON

- Accessing support:
    - User's support request JSON
    - Vendor's support response JSON

- Providing rating and submitting feedback:
    - User's rating/feedback submission JSON

## General Structure of the JSON
1. **Context field** (This is a part of the "Context" in the beckn protocol structure.)
    - `"domain"`: "dsep:advisory"
    - `"action"`: "search", "select", "support", "feedback" 
    - `"timestamp"`: the timestamp of the message
    - `"transaction_id"`: an ID generated for a particular chat session
    - `"language"`: "en" or any other supported language code

2. **Message field**
    - The contents of this field depend on the specific action in the user interaction flow.

## The Various JSON Files

1. `Search_Req`: User's search request
    - Message Field contains:
        - `"intent"`: 
            - `"category"`: The category of the user request (e.g., agriculture, technology, education)
            - `"item"`: The subject of the request or problem encountered
            - `"content-type"`: The type of content requested - `Video`, `PDF`, `Text`, `Audio`

2. `Search_Results`: System's response to search request
    - Message Field contains:
        - `"catalog"`: 
            - `"providers"`: An array of content providers
                - `"provider_id"`: Unique identifier for the provider
                - `"descriptor"`: Name of the provider
                - `"services"`: Array of content items with relevant details

3. `Consumption`: User's content selection
    - Message Field contains:
        - `"order"`: 
            - `"item"`: The selected content (video/pdf) with description and link
            - `"fulfillment"`: Content type and provider details

4. `Support`: User's support request
    - Message Field contains:
        - `"support-request"`: 
            - `"type"`: Type of support request (`Post-viewing Query`, `Technical Support`, `Content Clarification`, `Additional Resources`, `Expert Consultation`)
            - `"customer"`: Customer details (individual/organization)

5. `Support_Resp`: Agency's response to support request
    - Message Field contains:
        - `"support_response"`: 
            - `"ref_id"`: Reference ID for the request
            - `"type"`: Type of query with response
            - `"provider"`: Provider details

6. `Feedback`: User feedback
    - Message Field contains:
        - `"feedback"`: 
            - `"customer"`: Customer details
            - `"rating"`: Numerical rating
            - `"descriptor"`: Feedback comment