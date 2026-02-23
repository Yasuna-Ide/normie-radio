# NORMIE RADIO

**Generative Ambient Music from On-Chain Faces**

Each Normie's on-chain traits and 40×40 pixel bitmap are translated into a unique generative ambient composition. No two Normies sound the same.

## How It Works

### Pixel Data → Melody

The 40×40 monochrome bitmap is scanned column by column. Pixel density in each column determines the probability and pitch of notes — dense columns produce higher, louder tones. The face's silhouette directly shapes the melody.

### Trait → Sound Mapping

All 8 on-chain traits influence the music:

| Trait | Sound Parameter | Examples |
|-------|----------------|----------|
| **Type** | Scale | Human: Major, Cat: Pentatonic, Alien: Whole Tone, Agent: Minor |
| **Age** | Tempo & Octave | Young: fast/high, Old: slow/deep |
| **Gender** | Pitch Range | Male: low register, Female: high, Non-Binary: wide |
| **Hair Style** | Arpeggio Pattern | Afro: complex 7-step, Bald: minimal 2-step, Ponytail: ascending run |
| **Eyes** | Delay & Echo | Glowing Eyes: deep echo, Narrow Eyes: dry, Closed Eyes: spacious |
| **Facial Feature** | Harmonics & Timbre | Blush: bright/few overtones, Scar: dark/rich overtones |
| **Expression** | Reverb Depth | Sad: spacious, Serious: tight, Happy: moderate |
| **Accessory** | — | Reserved for future use |

### Daily Variation

A date-based seed subtly shifts the musical phrases each day, so the same Normie sounds slightly different tomorrow.

## Architecture

Single HTML file. No build tools, no dependencies, no backend.

- **Audio**: Web Audio API (oscillators, gain nodes, delay feedback)
- **Data**: [Normies API](https://api.normies.art) (pixels, traits)
- **RNG**: Mulberry32 seeded PRNG (deterministic per date + token ID)
- **Visual**: Canvas-based waveform analyzer

## Usage

1. Enter a Token ID (0–9999) or press **Random**
2. Press **Play** to start the generative music
3. Adjust volume with the **Vol** slider
4. Press **?** for the help overlay

## API

All data is fetched client-side from the public Normies API:

```
GET https://api.normies.art/normie/{id}/pixels    → 1600-char binary string
GET https://api.normies.art/normie/{id}/traits    → JSON with 8 trait attributes
GET https://api.normies.art/normie/{id}/image.png → 1000×1000 PNG
```

Rate limit: 60 requests/minute per IP.

## Credits

- **NORMIES** — On-chain generative faces by [@serc1n](https://x.com/serc1n) & [@yigitduman](https://x.com/yigitduman)
- **NORMIES RADIO** — Built with the [Normies API](https://api.normies.art)

## License

CC0
