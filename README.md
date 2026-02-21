# background-clarity

A scalar function that measures how well the background of a cat photograph supports the cat as the undisputed subject. It returns a score between 0 and 1 — where 1 means the background completely defers to the cat and 0 means the background competes with it.

## Input

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `cat_photo` | image | Yes | A photograph in which a cat is the intended subject. |

The photograph may depict any setting: a studio backdrop, a sunlit windowsill, a cluttered kitchen counter, a garden, or a city sidewalk. The function does not prefer one environment over another. What matters is how the visual information in the frame organizes itself around the cat.

## Output

A scalar score in **[0, 1]**.

- **Scores near 1.0** indicate backgrounds that are calm, tonally harmonious, and compositionally deferential — the cat commands the frame without competition.
- **Scores near 0.5** indicate mixed backgrounds where some elements support the subject but others create moderate distraction or tonal tension.
- **Scores near 0.0** indicate backgrounds that actively compete with the cat through heavy clutter, tonal clashes, or compositional rivalry that pulls the viewer's eye away from the subject.

## What It Evaluates

The function examines the photograph through three interlocking qualities. These are not independent axes averaged together; they are complementary lenses through which the same image is understood.

### 1. Visual Stillness

How free the background is from elements that generate their own demand for attention.

**Penalizes:**
- Physical clutter — tangled cords, scattered objects, stacked boxes, assorted packaging
- Busy patterns — bold wallpaper, high-contrast textures, strong geometric lines cutting across the frame
- Visible legible text — on packaging, signs, book covers, or screens (text is among the most aggressive attention magnets)
- Bright or heavily saturated color patches that act as individual eye magnets

**Rewards:**
- Backgrounds whose elements blend into a cohesive, quiet visual texture
- Spaces that are present without being busy — a bookshelf of uniform spines, a garden of soft repeating greenery
- Low-frequency visual rhythms that let the cat remain the loudest thing in the frame

**Key principle:** A clean background is not necessarily an empty one. A living room can appear behind a cat without disrupting the photograph, so long as its elements do not individually clamor for recognition.

### 2. Tonal Harmony

How well the background's colors, brightness, and contrast complement the cat rather than competing with it.

**Penalizes:**
- Neon-bright or heavily saturated walls and surfaces that overpower the subject
- Harsh lighting hot spots and extreme contrast jumps
- Patches of saturated color unrelated to the cat's fur
- Backgrounds that wash out the cat's edges and dissolve the boundary between figure and ground
- Other animals or partial figures in the frame — a second cat at the edge, a dog's nose from the corner, a person's hand reaching in — which fracture the sense of a single clear subject

**Rewards:**
- Soft, muted tones that sit comfortably behind the cat in brightness and saturation
- Colors that echo or complement the cat's fur — warm wood tones behind an orange tabby, cool grays behind a Russian Blue
- Clear visual separation between the cat and its surroundings, giving the subject primacy

### 3. Compositional Deference

How the spatial arrangement of background elements directs the viewer's eye toward the cat rather than away from it.

**Penalizes:**
- Strong lines leading off the edges of the frame, pulling the eye outward
- Bright windows or light sources positioned away from the cat that draw attention to the periphery
- Background elements arranged with their own internal logic (a neatly organized shelf, a deliberate row of plants) that constitute a secondary composition rivaling the cat

**Rewards:**
- Leading lines (the edge of a couch, converging lines of a hallway) that point toward the cat
- Depth-of-field blur that keeps the cat sharp while softening the background
- Natural framing elements (doorways, archways, the curve of a blanket) that enclose the cat within a visual boundary
- Backgrounds with enough structure to feel intentional but not so much that they become a composition of their own

## Use Cases

- **Content curation** — Social media platforms and cat content aggregators can use the score to surface photographs where the cat is the clear, uncontested subject.
- **Photography feedback** — Camera and editing applications can provide composition guidance, helping photographers understand how their background choices affect subject prominence.
- **Dataset construction** — Teams building training data for visual models can filter for images with clean, unambiguous compositions where the subject is unmistakable.
- **Automated judging** — Cat photography contests can incorporate background clarity as one dimension of evaluation alongside other compositional and aesthetic criteria.
- **Batch ranking** — Any workflow that needs to rank or sort a large set of cat photographs by visual clarity and subject prominence.

## Philosophy

The function is built on a single conviction: in a photograph of a cat, the cat should win. Not by obliterating everything around it, but by inhabiting a space arranged in its favor. A background is not judged as good or bad in isolation — it is judged as supportive or competitive in relation to the subject. The score is ultimately a measure of generosity: how generously the surrounding space gives itself over to the cat at its center.