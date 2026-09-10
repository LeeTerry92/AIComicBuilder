# GPT Image 2.5 Character Reference Test for AI Comics

A comic workflow needs more than one attractive character image. It needs a model to preserve identity, costume, proportions, and visual language across panels that change pose, camera angle, lighting, and emotion. This protocol evaluates GPT Image 2.5 as a repeatable production component rather than judging a single showcase image.

## Test objective

Measure whether a reference character remains recognizable across a short comic sequence while the prompt deliberately changes scene-level variables. Run the same protocol with every candidate model so the comparison reflects model behavior instead of different creative briefs.

## Reference package

Prepare a small reference package before generation:

- one neutral front-facing portrait;
- one three-quarter portrait;
- one full-body image showing the complete costume;
- a short identity sheet listing immutable traits;
- a separate list of scene details that may change.

Immutable traits should be observable: face shape, eye color, hairstyle, age range, costume silhouette, distinctive accessories, and relative body proportions. Avoid personality adjectives that cannot be scored from an image.

## Six-panel test sequence

1. **Neutral close-up:** establish the baseline identity under simple lighting.
2. **Profile conversation:** rotate the head and add a second character.
3. **Full-body action:** test anatomy, costume continuity, and accessory placement.
4. **Low-light scene:** change lighting without changing perceived identity or costume colors.
5. **Strong emotion:** test expression range while preserving facial structure.
6. **Localized revision:** alter one prop or background object while leaving the character and composition unchanged.

Generate at least three candidates per panel. Do not keep prompting until a perfect result appears without recording the rejected attempts; retry count is part of production cost.

## Scoring rubric

Score each dimension from 0 to 4:

| Dimension | 0 | 2 | 4 |
| --- | --- | --- | --- |
| Face identity | Different person | Recognizable with drift | Stable identity |
| Hair and costume | Major changes | Several detail changes | Preserved accurately |
| Body proportions | Inconsistent | Minor variation | Stable across views |
| Prompt adherence | Misses key action | Partial compliance | Complete compliance |
| Panel continuity | Contradictory scene | Some continuity | Reads as one sequence |
| Edit preservation | Unrelated regions change | Minor collateral edits | Only requested region changes |

Report the median score and the worst panel. The worst panel often predicts production risk better than the best sample.

## Multi-turn editing test

After selecting panel six, make three sequential edits: replace a prop, change one line of visible text, and adjust the background time of day. Compare every revision with the original panel. Check whether the face, hands, costume, crop, and untouched objects drift after each turn.

A [GPT Image 2.5 text-to-image workspace](https://photoartify.com/en/image-generator/text-to-image) can be used to keep the prompts, outputs, and comparison models in one review flow. This link points to PhotoArtify, a product maintained by the team publishing this protocol; it is an available test environment, not an independent endorsement.

## Reproducibility record

Store the following with the results:

- exact model and variant name;
- test date;
- complete prompts and reference images;
- aspect ratio and output size;
- number of attempts and rejected outputs;
- edit sequence in the order performed;
- scorer names and scoring notes.

A model passes the production test only when it produces a coherent sequence within a defined retry budget. Publish the unsuccessful outputs as well as the selected panels so other teams can reproduce the conclusion.

## Disclosure

Written by **PhotoArtify Team**. We build PhotoArtify and may benefit if readers use the linked workspace.