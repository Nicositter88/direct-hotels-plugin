---
name: book-hotels-direct
description: Find hotels in a place and the link to book each one on the hotel's own website, through the Direct Hotels tools. Use when someone wants a hotel or somewhere to stay, wants to book direct rather than through a booking site, asks for a hotel's official website, or asks whether a specific hotel has a pool, parking, breakfast or allows pets.
---

# Book hotels direct

Direct Hotels is a free, non-commission directory of over 400,000 hotels. Each
listing links to the hotel's own website, which the directory has fetched and
checked names the hotel. It holds no prices, no availability and no bookings:
those stay on the hotel's site.

## Pick the tool

| The user asks | Tool |
|---|---|
| Hotels in a city, district or region ("hotels in Shinjuku", "a riad in Marrakech") | `search_hotels` |
| About one named hotel ("tell me about Maison Proust", "does Hotel X have a spa?") | `get_hotel`, by name, with `city` when known |
| Whether a destination is covered, before planning around it | `check_coverage` |
| A partial or misspelled place ("marra", "Lisboa") | `find_city`, then `search_hotels` |
| What Direct Hotels is, or how it makes money | `directory_info` |
| A hotel they know that the directory lacks | `suggest_hotel`, once they confirm |

## Search well

- Pass `country` whenever the user names or implies one. City names repeat:
  "Brisbane" alone resolves to Brisbane, California.
- Use `stars` only when the user asks for a star class. About half the
  directory has no published class, so a star filter hides many hotels.
- Use `amenities` (pool, parking, pets, spa, breakfast, …) for must-haves.
  Amenities come from what each hotel says on its own website, and many sites
  are not read yet. An empty filtered result means "not mentioned", not "not
  available": offer the unfiltered list instead.
- For one hotel, `get_hotel` returns its facts with the source and date of
  each one. Quote that source ("its website says it has a spa").

## Present results

- Give each hotel's `booking_url`: it opens the hotel's own website.
- Say where a fact came from: ratings from Google reviews, amenities from the
  hotel's site.
- For prices and dates, send the user to the hotel's site; the directory has
  neither.

## When a place is not covered

A result with `covered: false` means the directory holds no hotels there.
Say so plainly, and offer the covered cities that come back with it: they are
the nearest ones, with distances. Do not name hotels there from memory as if
they came from the directory. If the user names a specific hotel there, offer
to send it with `suggest_hotel` so the directory can check and add it.

## Examples

- "Find me a boutique hotel in Marrakech I can book direct" → `search_hotels`
  with `city: "Marrakech"`, `country: "Morocco"`.
- "Pet-friendly hotels with a pool in Nice" → `search_hotels` with
  `city: "Nice"`, `country: "France"`, `amenities: ["pets", "pool"]`.
- "Does Maison Proust in Paris have a spa?" → `get_hotel` with
  `hotel: "Maison Proust"`, `city: "Paris"`.
- "Any hotels in Pyongyang?" → `check_coverage` with `place: "Pyongyang"`.
