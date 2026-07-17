# Toml (Tom's Obvious Minimal Language)

Welcome to the **Toml** project! This is an Android application built with Jetpack Compose, showcasing modern Android development practices.

## 🧐 What is TOML?

TOML stands for **Tom's Obvious, Minimal Language**. It is a configuration file format designed to be easy to read and write due to its simple and clear semantics.

### Why use TOML?
Think of TOML as a way to talk to your application using a "human-friendly" language. It's built to be minimal, meaning it doesn't have a lot of complex rules, and "obvious," meaning you can look at it and immediately understand what it's doing.

### Key Concepts in Simple Terms

1.  **Key-Value Pairs**: The foundation of TOML. It's just a name and a value assigned to it.
    ```toml
    title = "TOML Example"
    version = 1.0
    enabled = true
    ```

2.  **Tables (Sections)**: You can group related pieces of information together using square brackets.
    ```toml
    [owner]
    name = "Tom"
    dob = 1979-05-27T07:32:00Z # TOML supports dates too!
    ```

3.  **Arrays (Lists)**: Need a list of items? Just use square brackets.
    ```toml
    tags = ["programming", "config", "minimal"]
    ```

### TOML vs. Others
*   **JSON**: Can be hard for humans to read because of all the `{}` and `,`.
*   **YAML**: Clean, but very sensitive to spaces and indentation, which can lead to bugs.
*   **TOML**: Easy to read like YAML but strict and predictable like JSON.

## 🛠 How this project uses TOML
In modern Android development, TOML is the standard for **Gradle Version Catalogs**.
Check out `gradle/libs.versions.toml` in this project to see how we manage all our dependencies (like Compose and Hilt) in one clean, easy-to-read file.

### Understanding the Version Catalog (`libs.versions.toml`)

The catalog is split into several main sections:

1.  **`[versions]`**: This is where we define version numbers. Centralizing them here ensures that all libraries sharing a version (like Hilt components) stay in sync.
    *   *Example:* `hiltAndroid = "2.60"`

2.  **`[libraries]`**: This section defines the actual dependencies used in the project. You can define them in two ways:
    *   **`group` & `name`**: Splitting the dependency into the organization (**group**) and the specific component (**name**).
        *   *Example:* `group = "com.google.dagger"`, `name = "hilt-android"`
    *   **`module`**: Combining the group and name into a single string.
        *   *Example:* `module = "androidx.compose.ui:ui"`
    *   **`version.ref`**: A reference to a variable defined in the `[versions]` section. This allows you to update a version in one place and have it reflect everywhere.

3.  **`[plugins]`**: Used for Gradle plugins that provide build-level functionality.
    *   Uses an **`id`** (the unique plugin identifier) and a **`version.ref`**.

4.  **`[bundles]` (Optional)**: While not used in this project yet, bundles allow you to group multiple libraries together so you can import them with a single line in your build file.

### 💡 Pro Tip: Using it in your code

The best part about TOML catalogs is how they appear in your `build.gradle.kts` files. Gradle automatically converts the dashes (`-`) into dots (`.`).

*   In TOML: `androidx-compose-ui`
*   In Kotlin: `libs.androidx.compose.ui`

Example usage:
```kotlin
dependencies {
    implementation(libs.androidx.core.ktx)
    implementation(libs.hilt.android)
}
```

## 🚀 Tech Stack
*   **Kotlin**: The language of choice for Android.
*   **Jetpack Compose**: Android's modern toolkit for building native UI.
*   **Dagger Hilt**: Dependency injection to keep the code clean and testable.
*   **KSP**: Kotlin Symbol Processing for high-performance builds.

---
*Generated for the Toml Project.*
