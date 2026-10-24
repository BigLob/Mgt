# Archenemy App Plan

A phone app for playing Archenemy Commander (1 archenemy vs 3 heroes) with physical decks. The app runs the scheme deck and tracks life and poison. We assume everyone owns every scheme, so there is no collection tracking.

## How a game flows
1. The archenemy creates a game and gets a 4-letter room code.
2. The three heroes join on their phones with the code and a name. No accounts.
3. The archenemy builds or picks a scheme deck.
4. During play, every phone updates live.

## What each phone shows
- **Archenemy:** Set in Motion, Abandon ongoing schemes, view the deck.
- **Everyone:** the scheme just set in motion (large, with card image), ongoing schemes, both life totals, game log.
- **Heroes:** their own poison counter. Anyone can change life; every change is logged.

## Commander rules the app enforces
See `knowledge-base/archenemy-official-rules.md`.
- Archenemy starts at 60. The three heroes share one 60 life total.
- Poison is tracked per player; 10 loses.
- Scheme deck: 10+ cards, all different names.
- Warn on schemes that break with a shared life total (e.g. Mortal Flesh Is Weak).
- Presets for the four Duskmourn Commander scheme decks, plus "random 10".

## Tech
- **App:** React web app installable on phones (PWA), hosted free on Vercel or Netlify.
- **Live sync:** Firebase or Supabase realtime (free tier, no server code).
- **Card data:** Scryfall's free API for images and rules text.

### Setup needed from the owner
- Connect this repo to Vercel with a GitHub login (~5 min).
- Create a free Firebase project and share the config snippet (~5 min, only for sync).
- Friends just open the link and enter the room code.

## Build order
0. **Proof of concept (done first):** single phone, no hosting. Deck builder with presets, Set in Motion, ongoing tray, life and poison, log. See `app/`.
1. Deck builder and scheme display on a single device.
2. Room codes and live sync.
3. Life and poison tracking, plus the game log.
4. Polish: PWA install, offline card images.

## Later ideas
- Hero-phone prompts for schemes where players make choices (e.g. Choose Your Champion).
- Commander damage tracker (confirm how it works with a shared life total first).
- Supervillain Rumble mode.
