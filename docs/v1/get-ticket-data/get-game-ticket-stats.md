<script setup>
import SampleRequest from '../../components/SampleRequest.vue';
</script>

# Get Game Ticket Stats

A call to `API_GetTicketData` in this manner will retrieve ticket stats for a game, targeted by that game's unique ID.

[[toc]]

## HTTP Request

<SampleRequest httpVerb="GET">https://retroachievements.org/API/API_GetTicketData?g=1</SampleRequest>

### Query Parameters

| Name | Required? | Description                                                                  |
| :--- | :-------- | :--------------------------------------------------------------------------- |
| `z`  | Yes       | Your username.                                                               |
| `y`  | Yes       | Your web API key.                                                            |
| `g`  | Yes       | The target game ID.                                                          |
| `f`  |           | Set to 5 if you want ticket data for unofficial achievements.                |
| `d`  |           | Set to 1 if you want deep ticket metadata in the response's `Tickets` array. |

## Client Library

::: code-group

```ts [NodeJS]
import { buildAuthorization, getTicketData } from "@retroachievements/api";

// First, build your authorization object.
const userName = "<your username on RA>";
const webApiKey = "<your web API key>";

const authorization = buildAuthorization({ userName, webApiKey });

// Then, make the API call.
const gameTicketStats = await getTicketData(authorization, { gameId: 1 });
```

:::

## Response

::: code-group

```json [HTTP Response]
{
  "GameID": 14402,
  "GameTitle": "Dragster",
  "ConsoleName": "Atari 2600",
  "OpenTickets": 0,
  "URL": "https://retroachievements.org/ticketmanager.php?g=14402"
}
```

```json [NodeJS]
{
  "gameId": 14402,
  "gameTitle": "Dragster",
  "consoleName": "Atari 2600",
  "openTickets": 0,
  "url": "https://retroachievements.org/ticketmanager.php?g=14402"
}
```

:::

## Source

| Repo                     | URL                                                                                     |
| :----------------------- | :-------------------------------------------------------------------------------------- |
| RetroAchievements/RAWeb  | https://github.com/RetroAchievements/RAWeb/blob/master/public/API/API_GetTicketData.php |
| RetroAchievements/api-js | https://github.com/RetroAchievements/api-js/blob/main/src/ticket/getTicketData.ts       |