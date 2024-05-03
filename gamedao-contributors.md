# WIP

## airdrop calculations for contributors

the token claim tool will be used to calculate the airdrop for contributors.

contributors sign in with their email address and will receive an email with a link to the token claim tool.

the tool	is split into three evaluation sections:

	1. contribution
	2. conviction
	3. activity

```
native_address = az
evm_address = ez 
presale_price = p
hours_per_day = 8
base_token = 10

contribution_multiplier {

	cinv = tot_i / gen_i
	crev = tot_r / gen_r
	ctvl = tvl / gen_tvl

	# example: pow = 700 * 8 * 10 = 56000
	pow = total_time_days * hours_per_day * base_token

	return pow
}

contribution_drop = 1 * contribution_multiplier

# query social conviction

conviction_multiplier {

	conviction_mint_network = ( 100 = 4, 50 = 1, 0 = 0.25 )

	discord_member
	twitter_follower
	linkedin_follower
	linkedin_cv
	
	discord_activity = COUNT_EVENTS ( NOW-12M NOW )
	twitter_activity = COUNT_EVENTS ( NOW-12M NOW )
	linkedin_activity = COUNT_EVENTS ( NOW-12M NOW )

	github_follow = COUNT ( FROM REPOSITORIES )
	github_star = COUNT ( FROM REPOSITORIES )

	conviction_social = (
		discord_member +
		twitter_follower +
		linkedin_follower +
		linkedin_cv
	) x (
		discord_activity +
		twitter_activity +
		linkedin_activity +
		github_activity +
		github_follow +
		github_star
	) => ( result ) => result 

	return conviction_social * conviction_mint_network

}

# ( 1+1+1+1 = 4 ) x ( 10 + 10 + 10 + 100 + 1 + 1 = 132 ) x network ( 100 = 4 ) =
# 4 x 132 = 528 x network 4 =
# 10 x 2112 = 
# 21120 GAME

conviction_drop = total_time_days * hours_per_day * base_token * conviction_multiplier

# query for address + existing id

activity_multiplier {

	multiplier_has_native_address = HAS_NATIVE_ADDRESS x 1
	multiplier_testnet_id = HAS_TESTNET_ID(az) x 0.1
	multiplier_livenet_id = HAS_LIVENET_ID(az) x 0.25

	github_activity = COUNT ( FROM REPOSITORIES FROM COMMITS FROM NOW-12M )

	activity_token = days x hours_per_day x token_multiplier_work x ( multiplier_has_native_address + multiplier_testnet_id + multiplier_livenet_id )

}

```

