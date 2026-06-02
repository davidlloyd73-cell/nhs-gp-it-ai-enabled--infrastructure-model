# NHS GP IT — an AI-enabled infrastructure model

A reference architecture for AI in one NHS general practice, after the
EMIS/TPP duopoly. A set of single-file, dependency-free HTML pages that
**map out** the infrastructure and **demonstrate** the components that
didn't yet exist. Companion to the position paper
*"After EMIS — AI is dissolving the GP EMR duopoly"* (Lloyd, v2.5, May 2026),
grounded in the working Ridgeway Surgery prototype.

## The pages

| File | Page | What it is |
|---|---|---|
| **`index.html`** | **Map** | The landing page. An interactive map of the whole practice AI estate across the four architectural layers (intelligence feeds → patient vault → local inference → **boundary diode** → cloud assurance), wrapped in the governance layer. Every node is a real component or near-term gap; click to inspect its role, data classification and the repo that implements it. |
| `consultation.html` | Consultation | The animated one-episode-of-care mockup: vault access, Tortus scribing, local inference, allergy cross-reference, patient letter written back to the vault. |
| `assurance-harness.html` | Assurance | The **cloud assurance harness** as a working dashboard. Runs a synthetic-only sweep through the four-layer evaluation stack (deterministic safety checks → guideline-grounded RAG → frontier multi-grader critique → human adjudication) and produces a versioned assurance report for the clinical safety case. Never sees patient data. |
| `referral-pa.html` | Refer-to | The service-owned referral directory. Plain-English search returns one current service card — criteria, exclusions, route, attachments, freshness — with NHS / statutory / VCS tier badges, safeguarding banners, and an AI steward. |

## The architecture being mapped

1. **Patient vault** — patient is the primary rights-holder; clinical systems
   are licensees of scoped, time-limited access.
2. **Local clinical inference** — Qwen 2.5 32B on a Mac mini M4; identifiable
   data never leaves the practice perimeter.
3. **Boundary diode** — only synthetic outputs, structured metrics, model
   hashes and signed inbound templates may cross.
4. **Cloud assurance harness** — multi-grader benchmarking on synthetic and
   public material; never sees patient data.

Wrapped in a governance layer: DCB0129/0160 clinical safety case, DPIA, DSPT,
named clinical safety officer, immutable audit, and triadic-care attribution.

The map places the author's real repositories into their architectural layer —
`survivalemr`, `post-emis-mockup`, `diagnostic-teammate`, `consultation-analyzer`,
`refletter`, `Patient-Briefing`, `we-take-blood`, `WSIC_Anon` (de-identification
at the diode), `gp-population-simulator`, `gp-surgery-simulator` — see
[github.com/davidlloyd73-cell](https://github.com/davidlloyd73-cell).

## Run locally

```bash
python3 -m http.server 8000   # then visit http://localhost:8000
```

No build step, no dependencies. Deploys as a static site (e.g. Netlify) with
`index.html` as the entry point.

## Author

Dr David Lloyd — Salaried GP, Ridgeway Surgery, Harrow.
Prepared with Anthropic Claude per the method in Appendix A of the position
paper: locally-bounded AI for identifiable work, cloud frontier capability for
non-identifiable knowledge work and assurance.
