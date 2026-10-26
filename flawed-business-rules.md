# Flawed Enforcement of Business Rules (Coupon Abuse)

## Description
The application enforced a rule that prevented using the same coupon twice consecutively, but failed to prevent alternating between two different coupons. This allowed the total price to be reduced to zero.

## Steps to Reproduce
1. Added the expensive jacket to the cart.
2. Obtained two coupons: `NEWCUST5` and `SIGNUP30`.
3. In the cart, applied `NEWCUST5`, then `SIGNUP30`, then `NEWCUST5`, and so on (alternating).
4. The total price was reduced to `$0.00`.
5. Clicked "Place order" and the order was successful.

## Remediation
The server must track all coupons applied to a cart and prevent reusing any coupon more than once, regardless of the order of application.
