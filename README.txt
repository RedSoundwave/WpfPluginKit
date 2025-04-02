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
├── Assets/          # Stores images, icons, and other media resources.
├── Converters/      # Contains value converters for data binding.
├── Extensions/      # Stores extension methods for common functionalities.
├── Utility/         # Contains helper and utility classes.
├── ViewModels/      # Implements the MVVM pattern's ViewModel layer.
├── Views/           # Contains UI components such as pages and windows.
│   ├── Windows/     # Stores plugin-specific window components.
│   ├── Pages/       # Stores plugin-specific page components.
├── Resources/       # Contains XAML resource dictionaries and styles.
├── Services/        # Manages data access, business logic, and plugin interactions.
├── Models/          # Stores plugin-specific data models (if not in Shared project).
├── Commands/        # Implements custom ICommand logic for MVVM.
├── Behaviors/       # Contains attached behaviors for extended control functionality.
├── Interfaces/      # Defines common contracts for dependency injection and interaction.
├── Helpers/         # Utility classes for themes, serialization, etc.
├── Localization/    # Stores language resource files for multi-language support.
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