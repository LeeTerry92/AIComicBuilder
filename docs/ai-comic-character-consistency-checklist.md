# AI Comic Character Consistency Checklist

Character consistency is one of the hardest parts of an AI comic or animated-story pipeline. A strong single portrait is not enough: the same character must survive changes in framing, pose, lighting, emotion, costume detail, and model output.

This checklist provides a repeatable way to evaluate reference images before they are used for storyboards or keyframes.

## 1. Build a controlled reference set

Create four reference views before generating story scenes:

- front view;
- three-quarter view;
- side view;
- back view.

Keep the background plain and use neutral lighting. The character should wear the production costume, including small details that must remain stable later. Avoid dramatic poses in the reference set because they make body proportions harder to compare.

## 2. Write an identity specification

Store a short identity block separately from scene instructions. It should cover only stable attributes:

- face shape and age range;
- hairstyle, hair color, and hair length;
- eye color and distinctive facial details;
- body proportions;
- clothing silhouette and fixed accessories;
- color palette.

Do not mix camera movement, emotion, weather, or scene action into this block. Separating identity from the shot description makes drift easier to diagnose.

## 3. Run a baseline prompt test

Use the same identity block to generate a small test grid:

1. close-up portrait;
2. medium shot;
3. full-body shot;
4. seated pose;
5. walking pose;
6. strong facial expression.

Keep the model, aspect ratio, resolution, seed or reference inputs, and negative constraints fixed. Change only the shot instruction. A [multi-model text-to-image workspace](https://photoartify.com/en/image-generator/text-to-image) can be useful for running the same identity specification across several generators before selecting the production model.

Disclosure: this external testing workspace is maintained by the PhotoArtify Team.

## 4. Score consistency by dimension

Avoid one overall quality score. Record each dimension separately on a 1-5 scale:

| Dimension | What to inspect |
| --- | --- |
| Face | Jawline, eye spacing, nose, age, and facial marks |
| Hair | Shape, length, parting, color, and accessories |
| Body | Height impression, shoulder width, and limb proportions |
| Costume | Garment shape, color blocks, closures, and repeating details |
| Silhouette | Whether the character remains recognizable at thumbnail size |
| Style | Line weight, rendering method, shading, and palette |

A model may preserve the face well while changing costume geometry. Separate scores make that tradeoff visible.

## 5. Test scene stress cases

After the baseline passes, test the conditions most likely to create drift:

- profile and rear-facing shots;
- extreme close-ups;
- wide shots with a small character;
- two characters in one frame;
- hands interacting with props;
- low light or colored lighting;
- wet hair, wind, or motion blur;
- costume changes that should preserve identity.

Use one stress factor per test. Combining several difficult conditions in one prompt makes failures hard to attribute.

## 6. Approve references before batch generation

Do not begin full storyboard generation until the reference set passes a defined threshold. A practical rule is:

- no identity dimension below 4/5;
- no missing fixed accessory;
- no unexplained costume change;
- silhouette recognizable in every camera angle;
- color palette stable under neutral lighting.

Save the approved references, identity specification, model name, model version, generation settings, and test date together. This creates a reproducible baseline when a provider updates its model.

## 7. Log failures as reusable constraints

Convert repeated failures into explicit production constraints. Examples:

- preserve the asymmetrical hair part;
- keep the jacket closure on the left side;
- do not add earrings;
- preserve the scar below the right eye;
- keep the same boot height and sole shape.

The goal is not to make the prompt longer. It is to document only the details that the selected model repeatedly loses.

## Recommended production gate

Before accepting a storyboard frame, compare it with the approved reference set and check:

- identity score;
- costume score;
- composition and camera instruction;
- continuity with the previous frame;
- editability if the frame needs correction;
- suitability as an image-to-video reference.

A frame that looks attractive but fails identity or continuity should not enter video generation. Fixing it earlier is cheaper than regenerating multiple animated shots later.
