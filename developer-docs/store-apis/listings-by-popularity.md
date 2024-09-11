# Listings by Popularity

## Get Store Listings

{% swagger method="get" path="" baseUrl="https://store.novaplay.io/api/popularity" summary="Get Listings ordered by popularity" expanded="true" fullWidth="false" %}
{% swagger-description %}
This specific request is tailored to fetch a list of meticulously reviewed games, showcasing the best and most popular titles currently available.

This endpoint returns all games listed on NovaPlay, ordered by descending popularity.
{% endswagger-description %}

{% swagger-parameter in="query" name="verified" type="Boolean" %}
Returns games that are compatible with MetaMask in-game or MetaMask compatible marketplaces
{% endswagger-parameter %}

{% swagger-parameter in="query" name="metaMaskInGame" type="Boolean" %}
Returns games that support MetaMask in-game
{% endswagger-parameter %}

{% swagger-parameter in="query" name="metaMaskMarketplace" type="Boolean" %}
Returns games that have MetaMask compatible marketplaces
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Returns game listings" %}

{% endswagger-response %}
{% endswagger %}

#### Making the Request

{% tabs %}
{% tab title="Curl Request" %}
```bash
curl --location 'https://store.novaplay.io/api/popularity' \
--header 'Content-Type: application/json'
```
{% endtab %}

{% tab title="Response Type" %}
Here is the TypeScript type for the response:

```typescript
[{
	channels: [{
		channel_id: number;
		channel_name: string;
		release_meta: {
			name: string;
			meta_uri: string;
			platforms: {
				web: {
					name: string;
					external_url: string;
				};
				linux_amd64: {
					name: string;
					executable: string;
					installSize: string;
					processName: string;
					downloadSize: string;
					external_url: string;
					installScript: string;
				};
				darwin_amd64: {
					name: string;
					executable: string;
					installSize: string;
					processName: string;
					downloadSize: string;
					external_url: string;
					installScript: string;
				};
				windows_amd64: {
					name: string;
					executable: string;
					installSize: string;
					processName: string;
					downloadSize: string;
					external_url: string;
					installScript: string;
				};
			};
			project_id: string;
			release_id: string;
			description: string;
			external_url: string;
			release_name: string;
		};
		license_config: {
			id: string | null;
			tokens: boolean;
			access_codes: boolean;
		};
	}];
	disabled: boolean;
	account_id: string;
	isVerified: boolean;
	project_id: string;
	updated_at: Date;
	account_meta: {
		name: string;
		image: string;
		meta_uri: string;
		description: string;
		external_url: string;
	};
	account_name: string;
	project_meta: [{
		name: string;
		tags: string[];
		type: string;
		image: string;
		gallery: [{
			src: string;
			name: string;
			type: string;
		}];
		meta_uri: string;
		networks: {
			icon: string | null;
			name: string;
			type: string;
			address: string;
			chain_id: string;
			marketplace_urls: string[];
		};
		repository: string | null;
		description: string;
		discord_url: string;
		launch_epic: boolean;
		twitter_url: string;
		youtube_url: string | null;
		external_url: string;
		main_capsule: string;
		uses_overlay: boolean;
		is_novaplay_exclusive: boolean;
		wine_support: {
			mac: boolean;
			linux: boolean;
		};
		epic_game_url: string;
		launch_external: string | null;
		prompt_donation: string | null;
		donation_address: string | null;
		short_description: string;
		system_requirements: {
			cpu: string;
			gpu: string;
			disk: string;
			memory: string;
		};
	}];
	project_name: string;
}];
```
{% endtab %}
{% endtabs %}

#### Parameter combinations

When setting `verified=true`, only games that have _**either**_ in-game MetaMask support, _**or**_ MetaMask compatible marketplaces will be returned. This parameter is not necessary if using `metaMaskInGame` or `metaMaskMarketplace` separately.



When setting `metaMaskInGame=true`, only games that have in-game MetaMask support will be returned. This can be combined with `metaMaskMarketplace=true` to further narrow results.



When setting `metaMaskMarketplace=true`, only games that have MetaMask compatible marketplaces will be returned.



When combining `metaMaskInGame=true` with `metaMaskMarketplace=true`, only games that have _**both**_ in-game MetaMask support _**and**_ MetaMask compatible marketplaces will be returned. This is a more narrow set than just using `verified=true`.
