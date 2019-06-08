# How-to-identify-the-trial-and-paid-subscription-
How to identify the trial and paid subscription :

#1 iOS/macOS Platform 

For this we will check/verify [is_trial_period] key from receipt response.

(
    [quantity] => 1
    [product_id] => XXXXXXXXXXXXX
    [transaction_id] => XXXXXXXXXXXXX
    [original_transaction_id] => XXXXXXXXXXXXXX
    [purchase_date] => 2019-05-25 08:02:01 Etc/GMT
    [purchase_date_ms] => 1558771321000
    [purchase_date_pst] => 2019-05-25 01:02:01 America/Los_Angeles
    [original_purchase_date] => 2019-05-25 09:32:11 Etc/GMT
    [original_purchase_date_ms] => 1558776731000
    [original_purchase_date_pst] => 2019-05-25 02:32:11 America/Los_Angeles
    [expires_date] => 2019-05-25 08:07:01 Etc/GMT
    [expires_date_ms] => 1558771621000
    [expires_date_pst] => 2019-05-25 01:07:01 America/Los_Angeles
    [web_order_line_item_id] => XXXXXXXXXXXXXXXXXXX
    [is_trial_period] => false
    [is_in_intro_offer_period] => false
)

#2 Windows Platform:

For this we will check/verify [isTrial] key from receipt response.

[autoRenew] => 
[beneficiary] => nileshpatil@gmail.com
[expirationTime] => 2019-04-24T23:59:59.00+00:00
[expirationTimeWithGrace] => 2019-04-24T23:59:59.00+00:00
[id] => mdr:0:XXXXXXXXXXXXXXXXXXX:XXXXXXXXXXXXXXX
[isTrial] => 1
[lastModified] => 2019-04-25T10:52:53.46+00:00
[market] => IN
[productId] => XXXXXXXXXX
[skuId] => 0101
[startTime] => 2019-04-18T00:00:00.00+00:00
[recurrenceState] => Inactive

#3 Paypal :

For this in Paypal callback will check [txn_type] and [payment_status]

If [txn_type] => subscr_payment and [payment_status] => Completed then it will consider as Paid.
If [txn_type] => subscr_signup then it will consider as Trial.


#4 Android 

For Android there is 2 cases which we have found :

#1 In pub-sub we are getting [notificationType] = 'SUBSCRIPTION_RENEWED' and based on this we can identify and will make as paid but for newly purchased we are not getting details like purchased subscription is belong to trial and paid.

#2 We can identify the subscription type based on product name and initial purchase and expire purchase date.

Array
(
    [kind] => androidpublisher#subscriptionPurchase
    [initiationTimestampMsec] => 1556509012389
    [validUntilTimestampMsec] => 1562391405297
    [autoRenewing] => 1
)
