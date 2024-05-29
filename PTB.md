## example ptb
sui client ptb
--assign forge @$FORGE_ID
--assign to_address @$TO_ADDRESS
--move-call $PACKAGE_ID::my_module::new_sword forge 3 3
--assign sword
--transfer-objects "[sword]" to_address
--gas-budget 20000000

example public key = 0x1111111


## deploy package
sui client publish 

## set env vars 
export PACKAGE_ID=<id>
export HOUSE_CAP=<house_cap>
export MY_ADDRESS=<my_address>
export PUBLIC_KEY=0x1111111
export COIN_ID=<coin_id>

## init house_data
sui client ptb \
--preview \
--assign package @$PACKAGE_ID \
--assign house_cap @$HOUSE_CAP \
--assign public_key @$PUBLIC_KEY \
--assign coin_id @$COIN_ID \
--split-coins coin_id [1000000000] \
--assign coin \
--move-call $PACKAGE_ID::house_data::initialize_house_data house_cap coin public_key \
--gas-budget 50000000


sui client ptb \
--split-coins gas [1] \
--assign coin \
--transfer-objects [coin] @recipient_address \
--gas-budget 50000000



## mint counter

