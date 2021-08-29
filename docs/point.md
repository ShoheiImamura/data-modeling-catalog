```plantuml
' hide the spot
hide circle

' avoid problems with angled crows feet
skinparam linetype ortho

title: "ポ イ ン ト シ ス テ ム 案"

entity "ユ  ー  ザ  ー" as users {
    id
}

entity "販  売  ポ  イ  ン  ト" as point_products {
    id
    point_amount
    cach_amount
}


entity "注   文" as orders {
    id
}


entity "ポ  イ  ン  ト  可  換  商  品" as point_exchangeable_products {
    id
    amount
}


entity "獲  得  ポ  イ  ン  ト" as aquired_points {
    id
    user_id
    aquisition_div
    aquisition_id
    aquired_amount
    current_amount
    expiration_date
    timestamp
}

entity "減  算  ポ  イ  ン  ト" as subtracted_points {
    id
    subtraction_div
    subtraction_id
    aquired_point_id
    branch
    amount
    user_id
    timestamp
}

entity "ポ  イ  ン  ト  購  入  履  歴" as point_purchase_histories {
    id
    point_product_id
    user_id
    amount
    timestamp
}

entity "ポ  イ  ン  ト  贈  呈  履  歴" as point_giving_histories {
    id
    giver_id
    receiver_id
    amount
    timestamp
}


entity "ポ  イ  ン  ト  利  用  履  歴" as point_usage_histories {
    id
    user_id
    order_id
    amount
    timestamp
}

entity "ポ  イ  ン  ト  交  換  履  歴" as point_exchange_histories {
    id
    user_id
    point_exchangeable_product_id
    amount
    timestamp
}

users ||----o{ point_purchase_histories
point_products ||..o{ point_purchase_histories
users ||----o{ point_exchange_histories
point_exchangeable_products ||..o{ point_exchange_histories

users ||----o{ point_giving_histories
users ||----o{ point_giving_histories
users ||----o{ point_usage_histories
orders ||..o| point_usage_histories

users ||--o{ aquired_points

aquired_points ||..o| point_purchase_histories
aquired_points |o..o| point_giving_histories

subtracted_points }o...o| point_giving_histories
subtracted_points }o...o| point_exchange_histories
subtracted_points }o...o| point_usage_histories

aquired_points ||.o{ subtracted_points
```
