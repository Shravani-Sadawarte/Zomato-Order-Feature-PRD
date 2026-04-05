# Product Requirements Document (PRD)
## Multi-Restaurant Order Feature for Zomato

**Document Version:** 1.0  
**Last Updated:** April 5, 2026  
**Owner:** Product Management  
**Status:** Ready for Development  

---

## Executive Summary

This document outlines the requirements for implementing a **Multi-Restaurant Order** feature on Zomato. This feature will enable users to add items from multiple restaurants into a single order and checkout together, rather than being restricted to ordering from a single restaurant per transaction.

**Business Value:**
- Increase average order value (AOV)
- Improve user convenience for group orders or household purchases
- Enhance customer retention and engagement
- Differentiate Zomato from competitors
- Generate additional revenue through delivery optimization

---

## 1. Problem Statement

### Current State
Currently, Zomato users can only add items from a single restaurant to their cart at a time. If a user wants items from multiple restaurants, they must:
1. Complete a separate order with restaurant A
2. Initiate a new order for restaurant B
3. Potentially pay multiple delivery fees

### Pain Points
- **User Inconvenience:** Users purchasing for multiple people (family, friends, office) must place separate orders
- **Multiple Delivery Fees:** Customers pay separate delivery charges for each restaurant
- **Poor User Experience:** Cumbersome checkout process for bulk purchases
- **Missed Revenue:** Customers may abandon the app or use competitors
- **Operational Inefficiency:** Users may choose single large restaurants instead of multiple smaller ones

### Opportunity
- **Market Research:** 45% of users want to order from multiple restaurants in one go (internal user survey)
- **Competitor Analysis:** Swiggy and other players already support this feature
- **Revenue Impact:** Potential 15-20% increase in order frequency for multi-item purchasers

---

## 2. Goals & Success Metrics

### Primary Goals
1. Enable users to add items from up to 5 different restaurants in a single order
2. Provide seamless multi-restaurant checkout experience
3. Optimize delivery logistics for multi-restaurant orders
4. Maintain order fulfillment accuracy across multiple restaurants

### Success Metrics (OKRs)
| Metric | Target | Timeline |
|--------|--------|----------|
| Multi-restaurant order adoption rate | 8-10% of total orders | 6 months |
| Average order value (AOV) increase | +12-15% | 6 months |
| Average items per order | +1.5 items | 6 months |
| User retention improvement | +5% | 3 months |
| Feature discovery rate | 40%+ of active users | 3 months |
| Delivery fee optimization savings | 10% average per order | 6 months |
| User satisfaction score | 4.5+/5.0 | 3 months |

---

## 3. Feature Overview

### 3.1 Feature Name
**Multi-Restaurant Bundled Orders** (Internal: MRO)

### 3.2 Feature Description
A comprehensive shopping experience that allows users to:
- Browse and add items from multiple restaurants simultaneously
- View consolidated cart with items grouped by restaurant
- Manage items and quantities across different restaurants
- Select optimal delivery options for the combined order
- Pay once for the entire multi-restaurant order
- Track all restaurants' preparation and delivery status in real-time

### 3.3 Scope
#### In Scope
- Add/remove items from up to 5 restaurants per order
- Consolidated cart view with restaurant grouping
- Single checkout process with combined payment
- Smart delivery fee calculation for multi-restaurant routes
- Real-time order tracking across all restaurants
- Restaurant-wise status updates (Preparing/Ready/Picked up)
- Cancellation policy handling per restaurant
- Refund processing for multi-restaurant orders
- Post-order rating and feedback per restaurant

#### Out of Scope (Future Releases)
- Same delivery agent visiting multiple restaurants
- Restaurant co-branding/bundled promotions
- Pre-packed combo deals across restaurants
- Multi-restaurant subscription plans
- Dynamic pricing based on geographic clustering
- Scheduled multi-restaurant orders for future dates
- Cross-restaurant loyalty point pooling

---

## 4. User Stories & Use Cases

### Use Case 1: Family Group Order
**User:** Priya, planning dinner for her family  
**Scenario:**
- Priya wants appetizers from Restaurant A (Chinese)
- Her husband wants mains from Restaurant B (Indian)
- Kids want desserts from Restaurant C (Bakery)
- All should arrive together

**User Flow:**
1. Open Zomato app
2. Search and add items from Restaurant A
3. Access "Add from another restaurant" option
4. Search and add items from Restaurant B
5. Repeat for Restaurant C
6. Review consolidated cart (items grouped by restaurant)
7. Proceed to checkout
8. See combined delivery fee and total
9. Complete payment
10. Track all three restaurants' status simultaneously

**Expected Outcome:** Order placed successfully from 3 restaurants with single payment and one delivery charge

### Use Case 2: Office Lunch Order
**User:** Raj, ordering lunch for 5 office colleagues  
**Scenario:**
- 5 people have different food preferences
- Wants to collect money once and split payment
- Needs notification when all items arrive

**User Flow:**
1. Browse multiple restaurants based on colleagues' preferences
2. Add pizzas from Restaurant D
3. Add wraps from Restaurant E
4. Add salads from Restaurant F
5. View consolidated bill with itemized breakdown
6. See unified delivery window
7. Share order summary with office mates (optional)
8. Receive notification when entire order is ready

**Expected Outcome:** Multi-restaurant order placed, all items delivered, colleagues can settle payment

### Use Case 3: Shopping Errand
**User:** Anjali, shopping for household items  
**Scenario:**
- Wants groceries from one restaurant
- Branded items from another
- Bakery items from a third
- Single household delivery address

**User Flow:**
1. Add groceries from Grocery Store A
2. Add branded goods from Retail Restaurant B
3. Add fresh bread from Bakery C
4. View cart with 3 restaurant sections
5. Apply available coupons per restaurant
6. Proceed to single checkout
7. See one combined delivery fee
8. Track all three with one delivery agent

**Expected Outcome:** Efficient shopping with convenient delivery

---

## 5. Detailed Feature Specification

### 5.1 User Interface Components

#### 5.1.1 Multi-Restaurant Cart View
**Location:** Cart Screen  
**Design Elements:**
- **Restaurant Section Header:** Shows restaurant name, cuisine type, estimated delivery time
- **Item Listing:** Items grouped by restaurant with quantities, prices
- **Restaurant Actions:** 
  - Modify restaurant items
  - Remove entire restaurant section
  - View restaurant details/ratings
- **Visual Separators:** Clear separation between restaurant sections
- **Subtotal Per Restaurant:** Shows cost breakdown per restaurant
- **Collapsible Sections:** Users can collapse restaurants they're done reviewing

**Key Features:**
```
┌─ CART ──────────────────────────┐
│ Items from 3 restaurants         │
├─────────────────────────────────┤
│ 🍕 PIZZA PALACE        [►]       │
│  ├─ Margherita Pizza x2  ₹499   │
│  └─ Garlic Bread x1     ₹149    │
│    Subtotal: ₹648               │
├─────────────────────────────────┤
│ 🥗 SALAD CORNER        [►]       │
│  ├─ Caesar Salad x1     ₹299    │
│  └─ Dressing x1         ₹49     │
│    Subtotal: ₹348               │
├─────────────────────────────────┤
│ 🍰 SWEET TREATS        [►]       │
│  ├─ Chocolate Cake x1   ₹399    │
│  └─ Ice Cream x2        ₹199    │
│    Subtotal: ₹598               │
├─────────────────────────────────┤
│ TOTAL: ₹1,594                   │
│ Delivery: ₹45                   │
│ Taxes: ₹191                     │
│ GRAND TOTAL: ₹1,830            │
│                                 │
│ [CONTINUE TO CHECKOUT] ────────→│
└─────────────────────────────────┘
```

#### 5.1.2 Restaurant Picker Component
**Location:** After tapping "Add from another restaurant"  
**Elements:**
- Search bar with restaurant search
- Filter options (cuisine, delivery time, ratings)
- Recently added restaurants section
- Trending multi-restaurant combinations
- "View all restaurants" CTA
- Restaurant card showing:
  - Restaurant name
  - Cuisine type
  - Rating and review count
  - Delivery time
  - Delivery fee (if applicable for multi-restaurant order)
  - "Add items" button

#### 5.1.3 Unified Checkout Flow
**Location:** Checkout Screen  
**Elements:**
- **Order Summary:** 
  - Itemized breakdown per restaurant
  - Restaurant-wise subtotals
  - Per-item taxes if applicable
  
- **Delivery Details:**
  - Single delivery address
  - Expected delivery time (max of all restaurants' times)
  - Delivery fee optimization explanation
  - Delivery agent tracking available
  
- **Bill Breakdown:**
  - Subtotal of all items
  - Taxes (aggregated)
  - Delivery fee (optimized)
  - Promos/Coupons (per restaurant)
  - Loyalty points redemption
  - Grand Total
  
- **Payment Options:**
  - All standard Zomato payment methods
  - Wallet balance display
  - "Continue to Payment" button

#### 5.1.4 Real-time Tracking
**Location:** Order Status Screen  
**Elements:**
- Timeline showing status for each restaurant:
  - Order placed ✓
  - Confirmed by restaurant (time)
  - Preparing (progress indicator)
  - Ready for pickup (time)
  - Out for delivery (with agent track option)
  - Delivered ✓
  
- Estimated delivery time (aggregate)
- Individual restaurant contact info
- Customer support quick link
- Live map showing delivery agent location

---

### 5.2 Technical Specifications

#### 5.2.1 Cart Management
**Rules:**
- Maximum 5 restaurants per order
- Each restaurant can have up to 50 items in cart
- Minimum order value per restaurant: ₹200 (configurable)
- Maximum order value per order: ₹50,000 (configurable)
- One delivery address per order

**Validation:**
- Items must be currently available at restaurant
- Restaurant must be operational at checkout time
- Delivery area must cover all restaurants
- Items in cart persist for 30 minutes (with refresh notification)

#### 5.2.2 Delivery Fee Calculation
**Algorithm:**
```
1. Calculate direct delivery fee for each restaurant to user
2. Apply multi-restaurant optimization:
   - If restaurants are within 2km radius: 40% discount on additional fees
   - If restaurants are within 5km radius: 25% discount on additional fees
   - Beyond 5km: Standard per-restaurant fees apply
3. Ensure minimum delivery fee of ₹10 per restaurant
4. Cap total delivery fee at 15% of order value
5. Apply zone-based surge pricing if applicable
```

**Example:**
```
Restaurant A to User (alone): ₹60
Restaurant B to User (alone): ₹50
Restaurant C to User (alone): ₹45

Multi-restaurant optimization (within 2km):
Restaurant A: ₹60 (base)
Restaurant B: ₹50 × 0.6 = ₹30
Restaurant C: ₹45 × 0.6 = ₹27

Total: ₹117 (vs ₹155 if ordered separately)
Savings: ₹38 (24% savings for user)
```

#### 5.2.3 Order Processing Flow
```
User Checkout
    ↓
Validate all restaurants operational
    ↓
Validate all items in stock
    ↓
Create parent order + child orders (one per restaurant)
    ↓
Process payment (single transaction)
    ↓
Send order to each restaurant's kitchen system
    ↓
Send delivery request to logistics system
    ↓
Assign delivery agent considering multi-restaurant route
    ↓
Agent picks up from restaurants sequentially
    ↓
Agent delivers all items to user
    ↓
Mark all child orders as completed
```

#### 5.2.4 Database Schema Changes
**New Tables:**
```sql
-- Parent order for multi-restaurant orders
CREATE TABLE multi_restaurant_orders (
    id UUID PRIMARY KEY,
    user_id UUID NOT NULL,
    delivery_address_id UUID NOT NULL,
    total_amount DECIMAL(10,2),
    delivery_fee DECIMAL(7,2),
    tax_amount DECIMAL(7,2),
    status ENUM ('placed', 'confirmed', 'preparing', 'ready', 'delivered', 'cancelled'),
    created_at TIMESTAMP,
    delivery_agent_id UUID,
    estimated_delivery_time TIMESTAMP,
    actual_delivery_time TIMESTAMP
);

-- Child orders (one per restaurant)
CREATE TABLE order_items_by_restaurant (
    id UUID PRIMARY KEY,
    parent_order_id UUID NOT NULL,
    restaurant_id UUID NOT NULL,
    subtotal DECIMAL(10,2),
    status ENUM ('placed', 'confirmed', 'preparing', 'ready', 'picked_up', 'delivered'),
    restaurant_status_updated_at TIMESTAMP,
    FOREIGN KEY (parent_order_id) REFERENCES multi_restaurant_orders(id)
);
```

#### 5.2.5 API Endpoints
**New Endpoints:**
```
POST /api/v1/carts/add-restaurant
  - Add new restaurant to cart
  - Validate cart compatibility

POST /api/v1/orders/multi-restaurant
  - Create multi-restaurant order
  - Validate all items and restaurants
  - Calculate optimized delivery fee

GET /api/v1/orders/{orderId}/tracking
  - Get real-time tracking for all restaurants
  - Return aggregated status and timeline

GET /api/v1/orders/{orderId}/breakdown
  - Get itemized bill breakdown per restaurant
  - Return tax and discount details

POST /api/v1/orders/{orderId}/refund
  - Handle refunds for multi-restaurant orders
  - Refund per restaurant if needed

PUT /api/v1/orders/{orderId}/cancel
  - Cancel multi-restaurant order
  - Apply cancellation policy per restaurant
```

---

### 5.3 Cancellation & Refund Policy

#### 5.3.1 Cancellation Windows
| Scenario | Cancellation Allowed | Refund Amount |
|----------|---------------------|---------------|
| Within 2 min of order | Yes | 100% |
| 2-5 min (no restaurant confirmed) | Yes | 100% |
| After 1 restaurant confirmed | Partial | Full refund + penalty |
| All restaurants preparing | Partial | Reduced refund |
| >50% restaurants ready | No | No refund |

#### 5.3.2 Refund Processing
- Refunds processed per restaurant's policy
- Combined refund processed as single transaction to user wallet/card
- Timeline: 5-7 business days for card refunds

---

### 5.4 Safety & Quality Features

#### 5.4.1 Restaurant Qualification
Only restaurants meeting these criteria can be included in same order:
- Operational status: Active
- Approval status: Verified
- Minimum rating: 3.5 stars
- Cancellation rate: <5%
- Response time: <10 minutes average
- No temporary closure/holidays active

#### 5.4.2 Quality Assurance
- Items must have current availability in real-time
- Restaurant must confirm receipt within 5 minutes
- Delivery agent must confirm pickup from each restaurant
- Temperature-sensitive items require special packaging

#### 5.4.3 User Protections
- Order confirmation screenshot sent to user
- SMS/Notification at each major milestone
- Cancel-free window per restaurant order
- 24/7 customer support access
- Damage/missing items: Individual claims per restaurant
- Full order protection guarantee

---

## 6. User Experience Design

### 6.1 User Journey Map
```
Awareness
    ↓
    ├─ In-app banner "Order from multiple restaurants"
    ├─ Onboarding tooltip on cart page
    └─ Push notification campaign
    
Consideration
    ↓
    ├─ See "Add from another restaurant" button
    ├─ Educate on delivery fee savings
    └─ Show multi-restaurant suggestions
    
Decision
    ↓
    ├─ Add items from first restaurant
    ├─ Browse and add from 2nd, 3rd restaurants
    └─ Compare consolidated cart vs separate orders
    
Action
    ↓
    ├─ Proceed to unified checkout
    ├─ Complete payment
    └─ Receive order confirmation
    
Retention
    ↓
    ├─ Track all restaurants simultaneously
    ├─ Receive satisfaction survey
    └─ Enable reorder for same combo
```

### 6.2 Onboarding Strategy
1. **Phase 1 (Week 1):** Show tooltip on cart page for 20% of users
2. **Phase 2 (Week 2-3):** Expand to 50% of users, add educational content
3. **Phase 3 (Week 4+):** Full rollout with targeted notifications

### 6.3 Accessibility Considerations
- WCAG 2.1 AA compliance for all new screens
- Screen reader optimized for cart groupings
- High contrast mode for delivery time visualization
- Voice-over support for restaurant selection

---

## 7. Rollout & Release Strategy

### 7.1 Phased Rollout
```
Phase 1: Internal Testing (Week 1)
├─ Core team testing
├─ Load testing with 100 concurrent users
└─ Edge case identification

Phase 2: Beta (Weeks 2-3)
├─ 5% of active users in select cities (Delhi, Mumbai, Bangalore)
├─ Performance monitoring
├─ User feedback collection
└─ Bug fixes and iterations

Phase 3: Controlled Release (Weeks 4-5)
├─ 25% of user base across 10 major cities
├─ Real-world performance validation
├─ Customer support readiness check
└─ Business metrics tracking

Phase 4: Full Release (Week 6+)
├─ 100% of user base across all cities
├─ Optimization based on learnings
└─ Feature flag monitoring for instant rollback
```

### 7.2 Success Criteria for Each Phase
| Phase | Metric | Target | Pass Criteria |
|-------|--------|--------|---------------|
| Internal | Bug count | <20 | All critical bugs fixed |
| Alpha | Crash rate | <0.5% | Zero critical crashes |
| Beta | Adoption | >3% of beta users | >50% of invited users try feature |
| Beta | Satisfaction | 4.2+/5.0 | Positive user sentiment |
| Controlled | AOV increase | +8% | Order value increases |
| Controlled | System stability | 99.5% uptime | No outages >5 min |
| Full Release | Adoption | 8-10% | Target adoption achieved |

---

## 8. Competitive Analysis

### Market Landscape
| Feature | Swiggy | UberEats | Dunzo | Zomato (Current) |
|---------|--------|----------|-------|------------------|
| Multi-restaurant order | ✓ | ✓ | ✓ | ✗ |
| Delivery fee optimization | ✓ | ✓ | ✓ | - |
| Real-time tracking per restaurant | ✓ | Partial | ✓ | - |
| Max restaurants per order | 4 | 3 | 5 | - |

### Our Differentiation Points
1. **Superior UX:** Cleaner restaurant grouping in cart
2. **Better Delivery Optimization:** ML-based route optimization
3. **Faster Delivery:** Partnerships with delivery agents for multi-stop routes
4. **Better Analytics:** Detailed breakdown per restaurant
5. **Loyalty Integration:** Earn points across multiple restaurants
6. **Flexibility:** Support up to 5 restaurants vs competitors' 3-4

---

## 9. Marketing & Go-to-Market Strategy

### 9.1 Marketing Channels
1. **In-App Messaging:**
   - Contextual banner when users have multiple restaurants in browsing history
   - Tooltip on cart page
   - Push notifications with savings highlights
   
2. **Email Marketing:**
   - Dedicated email to frequent multi-order users
   - Highlight delivery fee savings (example: "Save ₹45 per order")
   - Segmented campaigns by user persona

3. **Social Media:**
   - Campaign: "Feed Your Cravings, Not Your Budget"
   - User-generated content of multi-restaurant orders
   - Influencer partnerships

4. **Paid Advertising:**
   - Google App Campaigns targeting "order from multiple restaurants" keywords
   - Instagram ads targeting group ordering scenarios
   - Retargeting ads for users who viewed multiple restaurants

### 9.2 Press & PR
- Press release highlighting feature launch
- Blog post: "The Future of Food Delivery: Multi-Restaurant Orders"
- Featured in tech publications and food media

### 9.3 Customer Education
- In-app tutorial video (30 seconds)
- FAQ section in help center
- Live chat support during rollout phase

---

## 10. Risks & Mitigation

### 10.1 Technical Risks

| Risk | Probability | Impact | Mitigation |
|------|-------------|--------|-----------|
| System overload during peak hours | Medium | High | Load testing, auto-scaling infrastructure |
| Payment failures for multi-transaction | Low | High | Robust transactional system, retry logic for failed payments |
| Data inconsistency across restaurants | Low | High | Database transactions, audit logs, reconciliation service |
| Integration failures with restaurant systems | Medium | Medium | API compatibility testing, fallback mechanisms |
| Delivery agent app crashes | Low | High | Comprehensive testing, staged rollout |

### 10.2 Operational Risks

| Risk | Probability | Impact | Mitigation |
|------|-------------|--------|-----------|
| Customer support volume spikes | High | Medium | Hire temp support staff, prepare FAQs, chat bot support |
| Restaurant order management issues | Medium | Medium | Restaurant training, simplified UI, support ticket system |
| Delivery delays due to multi-restaurant routing | Medium | Medium | Route optimization AI, backup logistics partners |
| Incorrect item delivery | Medium | Medium | QA checklists per restaurant, photographic verification |

### 10.3 Business Risks

| Risk | Probability | Impact | Mitigation |
|------|-------------|--------|-----------|
| Lower adoption than projected | Medium | Medium | Aggressive marketing, in-app incentives, A/B testing |
| Cannibalization of existing orders | Low | Low | Monitor AOV per order type, adjust incentives |
| Competitive response | High | Low | Continuous feature iteration, early mover advantage |
| Restaurant churn due to complexity | Low | Medium | Dedicated restaurant success team, training |

### 10.4 Contingency Plans
- **Feature Flag:** Instant disable if adoption <2% or critical bugs discovered
- **Gradual Rollback:** City-by-city rollback if performance degrades
- **Refund Program:** Automatic full refunds if order fails mid-delivery
- **Crisis Management:** Dedicated war room for resolving high-impact issues

---

## 11. Success Measurement & Analytics

### 11.1 Key Performance Indicators (KPIs)

#### Business Metrics
```
1. Adoption Metrics:
   - Multi-restaurant orders as % of total orders
   - New users trying MRO feature (% of active users)
   - Repeat MRO rate (% of users who order MRO 2+ times)

2. Revenue Metrics:
   - AOV for MRO vs single-restaurant orders
   - Additional delivery fee revenue
   - Incremental order volume from MRO

3. Retention Metrics:
   - 30-day retention of MRO users vs others
   - Engagement score for MRO users
   - Churn rate reduction post-launch

4. Customer Satisfaction:
   - NPS score for MRO orders
   - Rating distribution (expected 4.3+/5.0)
   - Complaint rate per order type
```

#### Product Metrics
```
1. Feature Usage:
   - Average # of restaurants per order (target: 2.8-3.2)
   - Average # of items from each restaurant
   - Peak usage times and days

2. Conversion Metrics:
   - % of users who see feature → click to add restaurant
   - % of users who add restaurant → complete order
   - Cart abandonment rate for MRO

3. Technical Metrics:
   - System uptime (target: 99.5%)
   - Order processing latency (<2 seconds)
   - Payment success rate (>99.5%)
   - Crash rate (<0.1%)
```

### 11.2 Analytics Dashboard
**Real-time Dashboard Metrics:**
- Active multi-restaurant orders
- Average delivery time by zone
- Payment success rate
- Customer support ticket volume
- Top restaurant combinations
- Technical health (CPU, memory, latency)

**Weekly Review Metrics:**
- Adoption trend
- AOV comparison: MRO vs single-restaurant
- Customer satisfaction scores
- Incident report and resolution time
- Business impact analysis

---

## 12. Development Roadmap

### Sprint Planning (6-Week Timeline)

#### Sprint 1: Foundation & Cart Management (Week 1-2)
- [ ] Database schema modifications
- [ ] Cart API modifications to support multiple restaurants
- [ ] Multi-restaurant validation logic
- [ ] Basic UI for restaurant selection
- **Deliverable:** Backend API for multi-restaurant cart

#### Sprint 2: Checkout & Payment (Week 2-3)
- [ ] Unified checkout flow implementation
- [ ] Delivery fee calculation engine
- [ ] Payment processing for combined orders
- [ ] Order creation and routing to restaurants
- **Deliverable:** End-to-end checkout flow

#### Sprint 3: Tracking & Integration (Week 3-4)
- [ ] Real-time order tracking system
- [ ] Restaurant kitchen display system integration
- [ ] Delivery agent app modifications
- [ ] Status update notifications
- **Deliverable:** Working order tracking

#### Sprint 4: Frontend & UX (Week 4-5)
- [ ] Multi-restaurant cart UI
- [ ] Checkout screen design & implementation
- [ ] Order tracking screen
- [ ] Onboarding tooltips & education
- **Deliverable:** Complete user-facing feature

#### Sprint 5: Quality & Testing (Week 5)
- [ ] End-to-end testing
- [ ] Performance optimization
- [ ] Security testing
- [ ] Load testing with 1000+ concurrent users
- **Deliverable:** Stable, tested feature

#### Sprint 6: Launch & Optimization (Week 6)
- [ ] Production deployment
- [ ] Monitoring and alerting setup
- [ ] Customer support training
- [ ] Marketing campaign launch
- **Deliverable:** Live feature with support

---

## 13. Resource Requirements

### Team Composition
```
Product:
- Product Manager (1) - Full-time
- Product Designer (1) - Full-time
- User Researcher (0.5) - Part-time

Engineering:
- Backend Engineers (2-3)
- Frontend Engineers (2)
- Mobile Engineers (iOS/Android) (1-2)
- DevOps/Infrastructure (1)

Operations:
- QA/QE Engineers (2)
- Restaurant Operations Manager (1)
- Customer Support Lead (1) - Full-time for 2 weeks

External:
- Design/Research agency (if needed for user studies)
```

### Estimated Budget
```
Engineering (6 weeks): $150,000-200,000
Design & Research: $25,000-40,000
Testing & QA: $30,000-40,000
Infrastructure & Tools: $15,000-20,000
Marketing & Launch: $40,000-60,000
Contingency (15%): $35,000-50,000

TOTAL: $295,000-410,000
```

---

## 14. Compliance & Legal

### 14.1 Terms & Conditions Updates
- Updated cancellation policy for multi-restaurant orders
- Liability allocation clarification (restaurant vs delivery vs app)
- Force majeure clauses for multi-restaurant failures

### 14.2 Data Privacy
- User addresses shared only with authorized delivery agents
- Restaurant data aggregation complies with data sharing agreements
- GDPR compliance for international users

### 14.3 Consumer Protection
- All existing consumer protection laws apply
- Individual restaurant responsibility for food quality
- Zomato's delivery guarantee applies to entire order
- Clear refund policy communication

---

## 15. Future Enhancements (Post-Launch)

### Phase 2 Features (Q3 2026)
1. **Smart Restaurant Bundling:** AI-powered restaurant recommendations
2. **Subscription Bundles:** Discount for pre-planned multi-restaurant combinations
3. **Schedule Orders:** Multi-restaurant orders for future delivery
4. **Split Payment:** Offer to split bill among multiple payers

### Phase 3 Features (Q4 2026)
1. **Multi-Restaurant Loyalty Programs:** Combined points across restaurants
2. **Dynamic Pricing:** Discounts for geographic clusters of restaurants
3. **Group Ordering Tool:** Create group orders with invite links
4. **Sustainability Options:** Consolidated packaging for eco-friendly delivery

### Phase 4 Features (2027+)
1. **Same Delivery Agent Multi-Stop:** One agent visits multiple restaurants
2. **Cross-Restaurant Meal Kits:** Pre-assembled multi-restaurant meals
3. **AI-Optimized Storage:** Smart delivery sequencing for temperature-sensitive items
4. **International Orders:** Multi-restaurant orders across different cities

---

## 16. Appendix

### 16.1 Glossary
- **MRO:** Multi-Restaurant Order
- **AOV:** Average Order Value
- **KPI:** Key Performance Indicator
- **NPS:** Net Promoter Score
- **OKR:** Objectives and Key Results
- **QA:** Quality Assurance
- **UX:** User Experience
- **API:** Application Programming Interface

### 16.2 Download Assumptions
- Zomato has 50M+ active monthly users
- 70% of users are in metro cities with adequate delivery infrastructure
- Average order frequency is 2 per month
- Delivery infrastructure can handle 2x current volume

### 16.3 Reference Materials
- [Competitor Feature Comparison](https://docs.google.com/sheets/...) [Insert Link]
- [User Research Summary](https://drive.google.com/...) [Insert Link]
- [Technical Architecture Diagram](https://miro.com/...) [Insert Link]
- [Design Mockups](https://www.figma.com/...) [Insert Link]
- [Financial Model](https://sheets.google.com/...) [Insert Link]

### 16.4 Document History
| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 0.1 | March 25, 2026 | PM Team | Initial draft |
| 0.5 | March 28, 2026 | PM Team | Stakeholder feedback incorporated |
| 0.8 | April 1, 2026 | PM Team | Design review changes |
| 1.0 | April 5, 2026 | PM Team | Final approval and ready for dev |

---

## 17. Approval Sign-off

| Role | Name | Date | Signature |
|------|------|------|-----------|
| Product Manager | [Name] | April 5, 2026 | _____ |
| Engineering Lead | [Name] | April 5, 2026 | _____ |
| Design Lead | [Name] | April 5, 2026 | _____ |
| Business Lead | [Name] | April 5, 2026 | _____ |
| Legal/Compliance | [Name] | April 5, 2026 | _____ |

---

**Document Status:** APPROVED FOR DEVELOPMENT  
**Next Review Date:** May 5, 2026 (Post-Beta Launch)  
**Questions or Feedback:** Please reach out to [product-team@zomato.com](mailto:product-team@zomato.com)

