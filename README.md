# Custom WPF Class Library Template

## Disclaimer
This template is designed for personal use and is tailored for a specific plugin architecture application. The rules and structure outlined in this document are applicable only in the context of this plugin system. If you intend to use this template for your own application, you are free to modify the rules, structure, or any other aspect to suit your requirements. Please ensure that any changes align with your own application needs and architecture.

## Overview
This template provides a structured approach for developing WPF plugins that include UI elements such as pages, windows, resources, and assets. The template ensures consistency across plugins and seamless integration with the main UI application.

## Rules & Guidelines

### 1. Consistent Dependencies & Styling
- All plugins **must** use the same NuGet packages as the main UI application.
- The same styles and resources should be maintained across all plugins to ensure a uniform user experience.
- Any additional dependencies should be discussed before integration to maintain compatibility.

### 2. MVVM Pattern Enforcement
- All plugins **must** follow the **MVVM (Model-View-ViewModel)** pattern.
- Direct logic in code-behind files should be avoided unless necessary for UI-specific actions.
- ViewModels should handle all business logic and communicate with Views via bindings and commands.

### 3. Documentation & Code Readability
- Every **class, method, property, and event** must include **XML summary comments** to ensure proper documentation.
- Use meaningful naming conventions for classes, methods, and variables.
- Avoid redundant or unused code to keep the project clean and maintainable.

### 4. Shared Models & Contracts
- A **Shared project** must be used for **models and contracts**, which will serve as a bridge between the main UI and all plugins.
- All plugins should reference this shared project rather than defining their own versions of models and contracts.
- The Shared project should be well-structured to avoid unnecessary dependencies.

### 5. Plugin Structure
Each plugin should maintain the following structure:
```
PluginName/
├── Assets/          # Stores media resources such as images, icons, sounds, and other visual or multimedia assets used by the plugin.
├── Converters/      # Contains value converters that are used to transform data during binding in XAML.
├── Extensions/      # Includes extension methods for commonly used functionalities or added features.
├── Utility/         # Contains general-purpose utility classes that support common operations across the plugin.
├── ViewModels/      # Implements the MVVM pattern’s ViewModel layer, which handles the logic and state of the UI.
│   ├── Windows/     # Stores ViewModels for plugin-specific window components.
│   ├── Pages/       # Stores ViewModels for plugin-specific page components.
├── Views/           # Contains UI elements, such as pages and windows, which make up the user interface of the plugin.
│   ├── Windows/     # Stores UI components for plugin-specific window views.
│   ├── Pages/       # Stores UI components for plugin-specific page views.
├── Resources/       # Contains shared XAML resource dictionaries, styles, and themes used across the plugin.
├── Services/        # Manages data access, business logic, and interactions with external services (e.g., APIs, databases).
├── Models/          # Defines data models specific to the plugin, or may use shared models from the Shared project.
├── Commands/        # Contains implementations of custom `ICommand` logic for use with MVVM, such as button clicks or other user actions.
├── Behaviors/       # Includes custom attached behaviors that enhance the functionality of existing controls.
├── Interfaces/      # Defines common contracts and interfaces, which may be used for dependency injection or for plugin interactions.
├── Helpers/         # Utility classes and methods for tasks such as theme management, serialization, file handling, etc.
├── Localization/    # Stores localization resources and language files to support multi-language plugins.

```

### 6. Plugin Loading & Registration
- Plugins should expose a main entry point that allows the host application to load and integrate the plugin seamlessly.
- The plugin system should support dependency injection where necessary.
- If plugins require additional services, they should be registered dynamically at runtime.

### 7. Performance & Best Practices
- Avoid memory leaks by properly unsubscribing from events and managing resources efficiently.
- Use asynchronous programming (`async/await`) where applicable to prevent UI blocking.
- Follow best practices for exception handling and logging to ensure better debugging and maintainability.

---
Following these guidelines will ensure a scalable, maintainable, and well-structured WPF plugin system. If any new rules or improvements are required, please discuss them before implementation.