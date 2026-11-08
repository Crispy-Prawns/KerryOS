# KerryOS
KerryOS is a virtual Kompanion app that allows you to raise and take care of your Kompanian while your Kompanian acts as a reflection of yourself that reminds you to do your goals all while you are having friendly fire with a rival of your similar level that you may befriend later to ascend together

# 🧈 KerryOS

**A habit tracker where your pet lives in a shared town.**

> **Hackathon Prompt 1:** *How can we leverage technology to promote health, social connection, and well-being in our communities?*

**Created by Moumita Rashid and Aria Moonsie**

KerryOS turns small daily habits (drink water, take your meds, check in on a neighbour) into something you can *see* and *share*. You pick a companion pet, set daily goals, and every goal you finish improves your pet's home. Your pet also lives in a live town alongside your neighbours' pets, so looking after yourself and looking out for others happen in the same place.

---

## Inspiration

Health habits are hard to keep when you're doing them alone, and loneliness hurts well-being just as much. The people who most need a check-in, like older neighbours, newcomers, or anyone having a rough week, are often the ones who go quiet. Most health apps only cover one side: either personal tracking or social features.

We wanted caring for yourself and caring for your community to be the same loop. We also wanted it to feel warm instead of clinical, so we gave the guilt to a pet. The pet gets hungry, cold, or proud, and you get to come back after a bad day without feeling judged.

## What it does

You pick a companion (cat, dog, fish, squirrel, bunny, or frog) and add daily goals. Each goal you finish earns **+2 comfort** and moves your pet up through six homes:

`Rainy Alley (0)` → `Cardboard Box (6)` → `Soft Blanket (16)` → `Cozy Cat Bed (30)` → `Tiny Apartment (50)` → `THE MANSION (80)`

Your pet's house sits on a live town map next to your neighbours' houses.

### 🩺 Health
- **Health-focused habit library:** take meds on time, log vitals or symptoms, book a check-up or telehealth visit, write questions for your next appointment, plus wellness basics like water, sleep, a 20-minute walk, and 10 minutes of mindfulness.
- **Plain-language health terms:** tap a term (*blood pressure, HbA1c, LDL cholesterol, telehealth, resting heart rate, anemia*) for a short everyday explanation. It includes a clear "general info only, not medical advice" note.
- **Custom goals:** add any daily goal you like.

### 🤝 Social connection
- **Town map:** see neighbours' houses, friends (💛), and who's online (🟢).
- **Town quest:** the whole town works toward a shared daily target. When it's hit, the town throws a festival 🎉.
- **Treats:** send a treat to a neighbour's pet to brighten their day.
- **Town chat:** short messages with replies, an online counter, and a friends-only option.
- **Friends:** search by name, send and accept requests, and see friends' homes highlighted.
- **Rival race:** a playful daily race against a rival pet for honey pots.
- **Empty lots:** open plots on the map invite you to bring a friend into the town.

### 🌱 Well-being, kind by design
- **Kind mode:** gentler pet messages, and a missed goal costs **1** comfort instead of **3**.
- **Rest days:** one rest token every 7 days protects your streaks and comfort when you need a break.
- **Let my pet sleep:** pause the nagging entirely.
- **Opt-in check-ins:** neighbours can check on you if you go quiet, but only if you leave the checkbox on, and you can turn it off any time.
- **Quiet-neighbour awareness:** houses show 💤 *quiet* after 1+ day and ⚠️ *unresponsive* after 2+ days. For opted-in neighbours, the town prompts a friendly "check in 💌".
- **Accessibility basics:** light and dark themes, `prefers-reduced-motion` support, and ARIA labels.

| Tab / Section | What it does |
|---|---|
| 🐾 **My habits** | Choose a companion, add goals, build streaks. |
| 🗺️ **Town map** | Your house, your neighbours' houses, online status, quiet flags, open lots. |
| 🏁 **Race** | Daily score out of 100 vs. a rival pet, honey pots, 7-day history. |
| 👥 **Friends** | Find people, handle requests, view your friend list. |
| 🌱 **Habit picker** | Ready-made habits: *Connect*, *Wellness*, *Care access*. |
| 🩺 **Health terms** | Plain-language glossary with a medical disclaimer. |
| 🎪 **Town quest** | A shared goal for the whole town. |
| 💬 **Town chat** | Floating chat with replies and a friends-only toggle. |

Missed goals cost comfort at the next daily reset, unless you used a rest day or Kind mode. The **Next day (demo)** button in the footer previews the daily rollover without waiting until tomorrow.

## How we built it

KerryOS is a single self-contained HTML file with vanilla JavaScript: no framework and no build step.

- **Personal progress:** stored in the browser's `localStorage`, with daily reset logic for streaks, penalties, and rest tokens.
- **Shared town:** friends, chat, treats, and presence use the `window.claude` runtime (`user`, `db`, and `room`), with live `onSnapshot` listeners on `town` and `chat` collections.
- **Art:** hand-painted backgrounds for each home tier, pixel-art pets, and inline SVG pets in the race scene, with CSS animations.
- **Theming:** CSS variables for light and dark mode. Fonts are Baloo 2 and Nunito.
- **Privacy by design:** the shared town only receives summary data: pet name, pet type, comfort, house tier, a *count* of goals done vs. total, last-active time, treats sent, friend list, and your check-in opt-in. The text of your goals stays on your device.

## Challenges we ran into

- **Tone.** A dramatic, nagging pet is funny, but it can feel bad on a hard day. Kind mode, rest days, and a sleep toggle let the app motivate without shaming.
- **Social features without exposing people.** We settled on sharing summary counts only, and made neighbour check-ins opt-in.
- **Detecting quiet neighbours fairly.** We used time thresholds plus the opt-in so people aren't flagged for simply taking a day off.
- **A shared town from one file.** Live data, presence, friend requests, and friends-only chat all had to work with no backend of our own.
- **Testing a once-a-day loop.** We added the "Next day (demo)" button so the rollover is easy to test and show.

## Accomplishments that we're proud of

- Putting self-care and community care in one loop instead of two separate apps.
- A kind-by-design approach: Kind mode, rest tokens, and an opt-in safety net for people who go quiet.
- A working multiplayer town with live presence, friends, treats, chat, and a shared quest, all in a single HTML file.
- Plain-language health info with a clear disclaimer.
- Accessibility basics: dark mode, reduced-motion support, and ARIA labels.

## What we learned

- Warm, playful design makes people more willing to engage with health habits than a clinical tracker does.
- Opt-in and minimal data sharing need to be designed in from the start, not added later.
- Even a small app needs decisions about how it treats people on their bad days, not just their good ones.
- Designing for a community means handling the quiet users as carefully as the active ones.

## What's next for KerryOS

- **Safety:** chat reporting and blocking before any real community rollout. Chat currently has a 140-character limit and a send-rate limit, but no moderation tools.
- **Reach:** push or SMS reminders for people who don't open the app.
- **Real-world links:** connect the care-access habits to local clinics, community centres, and volunteer groups.
- **Accessibility:** screen-reader testing, larger-text options, and translations.
- **Offline-first sync:** queue treats and messages sent while offline.
- **Organiser insights:** optional anonymised community stats, such as how many neighbours checked in this week.

---

## Running it

**Solo mode (anywhere):** open `KerryOS.html` in any modern browser. Habits, comfort, tiers, Kind mode, rest days, the health glossary, and the rival race all work offline. No install needed.

```bash
open KerryOS.html        # macOS
xdg-open KerryOS.html    # Linux
start KerryOS.html       # Windows
```

**Town mode (live neighbours):** the shared town, friends, chat, and presence need the Claude artifact runtime, so the page has to be published as an artifact with the user signed in. Outside of that runtime, KerryOS stays in solo mode and shows *"The town lights up once the page is published."* Hosting the file on GitHub Pages therefore gives solo mode only.

## Privacy

- Your goals and their text stay on your device.
- The shared town only receives the summary data listed above.
- Neighbour check-ins are opt-in and can be turned off at any time.
- Health information in the app is general education only. KerryOS does not collect medical data.

## Repository contents

| File | Description |
|---|---|
| `KerryOS.html` | The whole app |
| `KerryOS_thumbnail.png` | Project thumbnail |
| `README.md` | This file |

## Credits

Built by **Moumita Rashid** and **Aria Moonsie** for the hackathon under Prompt 1 (health, social connection, and well-being). The rival race is adapted from an earlier project, *Honey Nap*.
