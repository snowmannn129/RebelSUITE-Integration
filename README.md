# RebelSUITE-Integration

## Overview

RebelSUITE-Integration is the central repository for integration resources, shared libraries, and cross-component documentation for the RebelSUITE ecosystem. It provides the foundation for seamless integration between all RebelSUITE components.

## Purpose

This repository serves several key purposes:

1. **Shared Resources**: Centralized location for assets, libraries, and utilities used across multiple RebelSUITE components
2. **Integration Documentation**: Comprehensive guides for integrating different RebelSUITE components
3. **Cross-Component Testing**: Framework and tools for testing interactions between components
4. **Compatibility Management**: Tracking compatibility between different versions of RebelSUITE components
5. **Integration Scripts**: Utilities for automating cross-component workflows

## Repository Structure

```
RebelSUITE-Integration/
├── shared/              # Shared resources
│   ├── assets/          # Shared assets (icons, fonts, etc.)
│   ├── libraries/       # Shared code libraries
│   ├── formats/         # Shared file format definitions
│   └── scripts/         # Shared scripts
├── docs/                # Integration documentation
│   ├── integration-framework.md
│   ├── cross-testing-guide.md
│   └── shared-resources.md
├── tests/               # Cross-component tests
├── scripts/             # Integration scripts
├── .github/             # GitHub workflows and templates
├── .gitignore           # Git ignore file
└── README.md            # This file
```

## RebelSUITE Components

The RebelSUITE ecosystem consists of the following components, each with its own repository:

1. [**RebelDESK**](https://github.com/snowmannn129/RebelDESK): A lightweight, modular IDE with AI-assisted coding capabilities
2. [**RebelCAD**](https://github.com/snowmannn129/RebelCAD): A comprehensive CAD/3D modeling software
3. [**RebelCODE**](https://github.com/snowmannn129/RebelCODE): A coding and scripting environment
4. [**RebelENGINE**](https://github.com/snowmannn129/RebelENGINE): A game development engine
5. [**RebelFLOW**](https://github.com/snowmannn129/RebelFLOW): A node-based automation tool

## Integration Mechanisms

RebelSUITE components integrate through several mechanisms:

### 1. Shared File Formats

Common file formats enable seamless data exchange between components:
- 3D model formats (.fbx, .obj, .gltf)
- Script formats (.py, .js, .ts)
- Workflow definitions (.flow)
- Project files (.rproj)

### 2. Plugin Architecture

Each component implements a plugin system that allows other components to extend its functionality.

### 3. Inter-Process Communication (IPC)

Components communicate through standardized IPC mechanisms:
- Socket-based communication
- Shared memory
- File-based communication
- REST APIs
- Event system

### 4. Shared Libraries

Common code libraries provide consistent functionality across components:
- Math utilities
- UI components
- File I/O
- Networking
- Configuration

## Using This Repository

### As a Git Submodule

You can include this repository as a submodule in other RebelSUITE component repositories:

```bash
git submodule add https://github.com/snowmannn129/RebelSUITE-Integration.git shared
```

### As a Package Dependency

For JavaScript/TypeScript components, you can include shared libraries as a package dependency:

```json
{
  "dependencies": {
    "rebelsuite-shared": "github:snowmannn129/RebelSUITE-Integration#main/shared/libraries"
  }
}
```

### As a CMake External Project

For C++ components, you can include shared libraries using CMake's ExternalProject:

```cmake
include(ExternalProject)
ExternalProject_Add(
  rebelsuite-shared
  GIT_REPOSITORY https://github.com/snowmannn129/RebelSUITE-Integration.git
  GIT_TAG main
  SOURCE_SUBDIR shared/libraries
)
```

## Documentation

For detailed information about RebelSUITE integration, refer to the following documents:

- [Integration Framework](docs/integration-framework.md): Overview of the integration architecture
- [Cross-Testing Guide](docs/cross-testing-guide.md): Guide for testing interactions between components
- [Shared Resources](docs/shared-resources.md): Documentation of shared libraries and assets

## Contributing

Contributions to RebelSUITE-Integration are welcome! Please see our [Contributing Guide](.github/CONTRIBUTING.md) for more information.

## License

RebelSUITE-Integration is licensed under the [MIT License](LICENSE).

## Contact

For questions or support, please contact the RebelSUITE team at [support@rebelsuite.com](mailto:support@rebelsuite.com).
