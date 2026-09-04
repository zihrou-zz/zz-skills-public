---
name: photo-texture-cleanup
description: Prevent and repair unnatural grid, crosshatch, waxy, mottled, painterly, or repeated-pattern artifacts in generated or edited photographs. Use for photorealistic image generation, retouching, restoration, object removal, background replacement, extension, or upscaling. Do not use for illustrations, diagrams, screenshots, or intentionally stylized artwork.
---

# Photo Texture Cleanup

Preserve a believable camera-made photograph while completing the user's requested edit. Use the original or earliest available photo as the texture source of truth, and minimize generative reconstruction.

## Choose the repair method

Use the least generative method that can solve the defect:

1. For crop, rotation, exposure, white balance, or geometry-only changes, use deterministic image processing.
2. For small marks or defects on flat backgrounds, use local cloning, interpolation, or tightly bounded inpainting with feathered edges and matched grain.
3. For object removal or missing scene content, make one generative edit from the original and protect everything outside the edit mask.
4. If texture artifacts appear after generation, stop full-image regeneration. Recover aligned texture from the original where possible; otherwise use restrained local filtering and subtle non-periodic monochrome grain.

Never blur the whole image to conceal artifacts. Avoid repeatedly using an AI-edited result as the source for another full-image generation pass.

## Prompt invariants

For photorealistic work, explicitly request natural, non-repeating camera texture and reject:

- grid, crosshatch, woven, fingerprint-like, rippled, worm-like, orange-peel, stippled, embossed, blotchy, smeared, painterly, over-sharpened, waxy, plastic, or repeated textures;
- synthetic pores, airbrushed skin, painted hair ridges, patterned wall noise, repeated wood grain, and invented fabric weave.

When people are present, preserve identity, facial structure, expression, anatomy, pose, hands, fingers, skin tone, hair, clothing, tattoos, jewelry, and accessories. Require coherent pores, fine hairs, natural creases, smooth tonal transitions, plausible contact shadows, individual hair strands, and natural hair clumping. Do not beautify or airbrush unless requested.

For image editing, state that pixels outside the target region must remain unchanged. Do not alter people merely because the background or an object is being edited.

## Local repair rules

- Keep masks as narrow as practical and feather their boundaries.
- Match local luminance, color, sharpness, noise level, and depth of field.
- Use irregular, non-periodic grain; never introduce a tiled texture.
- Prefer one localized correction or a return to the original over continuing a degraded edit chain.
- Reject results with visible patches, halos, duplicated objects, identity changes, warped anatomy, smeared text, mismatched grain, color shifts, or collateral edits.

## Required QA

Inspect the whole image at normal size and suspicious areas at 100–200% zoom. Prioritize faces, necks, hands, fingers, arms, tattoos, hair, clothing edges, pale walls, ceilings, skies, tabletops, fabric, dark screens, edit boundaries, and reconstructed regions.

Compare with the original when available. Look for periodic lines, crosshatching, mottling, waxy skin, invented pores, smeared edges, seams, repeated details, and geometry changes. Deliver only a result that passes both normal-view and zoomed inspection. If a tradeoff cannot be removed without damaging the photo, explain it briefly instead of hiding it.
