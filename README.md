## Learning Process and Observations

While building this project, I used my previous **Happy Birthday Compose App** as a reference because many concepts were similar, such as Images, Text, Modifiers, and Composable functions.

Initially, I approached the Article screen with the same mindset as the Happy Birthday project. Since the Birthday app used a `Box` layout to place text on top of an image, I started thinking along the same lines.

However, after comparing the expected output with my preview, I realized that the Article screen had a completely different layout structure.

### Why I Changed from Box to Column

**Happy Birthday App**

* Image is used as a background.
* Text is displayed on top of the image.
* `Box` is the correct choice because the elements need to overlap.

**Compose Article App**

* Image is displayed first.
* Title appears below the image.
* Paragraphs appear below the title.
* No overlapping is required.
* `Column` is the correct choice because elements are arranged vertically.

As soon as I realized the output required a vertical arrangement instead of overlapping content, I replaced `Box` with `Column`, and the layout immediately matched the expected design.

### Text Alignment Learning

Initially, I used:

```kotlin
Modifier.align(Alignment.CenterHorizontally)
```

Later, after comparing my solution with the official solution, I learned that this only changes the position of the Text composable inside its parent layout.

The official solution used:

```kotlin
textAlign = TextAlign.Justify
```

This formats the text itself and makes paragraphs look like a proper article.

**Key takeaway:**

* `Modifier.align(...)` → Layout alignment
* `TextAlign.Justify` → Text formatting

### My Solution vs Official Solution

My approach:

* Created separate composables:

  * `ComposeArticleImage()`
  * `ComposeArticleText()`

Official solution:

* Used a single composable (`ArticleCard`) containing both the Image and Text components.

Observation:

* Both approaches work correctly.
* The official solution is more compact for a small screen.
* My approach helped me better understand composable decomposition and component separation.

### Modifier Learning

While comparing my code with the official solution, I noticed the common Compose pattern:

```kotlin
modifier: Modifier = Modifier
```

and later:

```kotlin
Column(modifier = modifier)
```

I learned that:

* This is a standard Compose convention.
* It allows composables to be customized by their caller.
* If a modifier parameter is declared but never used, Android Studio shows:

  * `Parameter 'modifier' is never used`

### Additional Observation

The layout looked slightly different in the emulator compared to the expected output.

After testing on a real device, the UI matched the expected design.

This taught me that:

* Compose Preview
* Android Emulator
* Physical Device

can sometimes display UI slightly differently due to system UI, display cutouts, and device-specific settings.
