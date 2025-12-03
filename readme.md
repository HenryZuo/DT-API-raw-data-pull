# Data Thistle API Explorer (v2 – Working & Up-to-date)

A tiny, standalone TypeScript script designed **exclusively** to explore the real shape of event data returned by the official Data Thistle API.

Use this tool only during the prototyping phase to:
- See the exact structure of real events (nesting, field names, date formats, images, tickets, venues, etc.)
- Make confident decisions about your Zod schema and data transformation logic

Once you’ve inspected the real data, you can safely delete this folder — it’s intentionally disposable.

### What you’ll get when you run it

- The first 3 real events printed beautifully in the terminal
- A complete raw API response saved as `datathistle-full-response.json`
- Immediate clarity on how Data Thistle structures events, performances, places, tags, prices, etc.

### Prerequisites

- Node.js ≥ 18
- A free Data Thistle API key (JWT token)

### Quick Start (< 2 minutes)

```bash
# 1. Clone or copy this folder
git clone <repo> dtapi-explore && cd dtapi-explore
# or just create a new folder and copy the files in

# 2. Install dependencies
npm install

# 3. Copy the example env file
cp .env.example .env
```

### Get your API key

1. Go to https://api.datathistle.com
2. Log in / register (free)
3. Go to your account → API Keys
4. Copy the JWT token

### Add your key

Edit `.env` and paste your token:

```env
DATATHISTLE_API_KEY=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.xxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

### Run the explorer

```bash
npm run explore
```

### Customising the query (optional)

Open `explore.ts` and edit the `buildQueryParams()` function.  
Some useful filters you can try (uncomment one at a time):

```ts
params.append('town', 'London');
params.append('town', 'Edinburgh');
params.append('tags', 'christmas');
params.append('tags', 'comedy,!film');        // include comedy, exclude film
params.append('name', 'panto');              // substring search in event name
// params.delete('tags');                    // remove tag filter completely
```

Just save the file and re-run `npm run explore`.

### Output files

- `datathistle-full-response.json` → full raw API payload (open in VS Code with Prettier/JSON viewer)

### Project scripts

```json
{
  "scripts": {
    "explore": "ts-node explore.ts"
  }
}
```

### Dependencies (already in package.json)

```bash
npm install axios dotenv
npm install -D ts-node typescript @types/node
```

### That’s it!

Once you’ve seen the real data structure, paste one complete event object (or just say “I’ve got the data!”) and I’ll instantly give you:

- A bullet-proof Zod schema
- A clean transformer to your internal `Activity` format
- The Next.js API route + cron logic

Happy exploring – you’re now 100% unblocked!