# RebelSUITE Shared Resources and Libraries

## Overview

This document outlines the shared resources, libraries, and utilities used across the RebelSUITE ecosystem. By centralizing common functionality and resources, RebelSUITE ensures consistency, reduces duplication, and simplifies maintenance across all components.

## Directory Structure

Shared resources are organized in a central location accessible to all RebelSUITE components:

```
C:\Users\snowm\Desktop\VSCode\RebelSUITE\
├── shared/                      # Shared resources root directory
│   ├── assets/                  # Shared assets
│   │   ├── icons/               # Common icons
│   │   ├── fonts/               # Common fonts
│   │   ├── themes/              # Theme definitions
│   │   ├── models/              # Common 3D models
│   │   ├── textures/            # Common textures
│   ├── libraries/               # Shared code libraries
│   │   ├── core/                # Core utilities
│   │   ├── ui/                  # UI components
│   │   ├── math/                # Math utilities
│   │   ├── io/                  # I/O utilities
│   │   ├── network/             # Networking utilities
│   ├── formats/                 # Shared file format definitions
│   │   ├── model/               # Model format specifications
│   │   ├── project/             # Project format specifications
│   │   ├── workflow/            # Workflow format specifications
│   │   ├── script/              # Script format specifications
│   ├── scripts/                 # Shared scripts
│   │   ├── build/               # Build scripts
│   │   ├── test/                # Test scripts
│   │   ├── deploy/              # Deployment scripts
│   │   ├── utils/               # Utility scripts
│   ├── docs/                    # Shared documentation
│   │   ├── api/                 # API documentation
│   │   ├── formats/             # Format documentation
│   │   ├── integration/         # Integration documentation
│   │   ├── style-guides/        # Style guides
```

## Shared Libraries

### 1. Core Utilities

Core utilities provide fundamental functionality used across all components:

#### Math Library
- Vector and matrix operations
- Quaternion handling
- Geometric calculations
- Interpolation functions
- Random number generation

```cpp
// C++ example
#include "shared/libraries/core/math/vector.h"

Vector3 position(1.0f, 2.0f, 3.0f);
Vector3 direction(0.0f, 1.0f, 0.0f);
float distance = position.distance(direction);
```

```python
# Python example
from shared.libraries.core.math.vector import Vector3

position = Vector3(1.0, 2.0, 3.0)
direction = Vector3(0.0, 1.0, 0.0)
distance = position.distance(direction)
```

```typescript
// TypeScript example
import { Vector3 } from 'shared/libraries/core/math/vector';

const position = new Vector3(1.0, 2.0, 3.0);
const direction = new Vector3(0.0, 1.0, 0.0);
const distance = position.distance(direction);
```

#### Logging System
- Consistent logging across all components
- Log levels (debug, info, warning, error)
- Log formatting and output options
- Log filtering and searching

```cpp
// C++ example
#include "shared/libraries/core/logging/logger.h"

Logger::debug("Initializing component");
Logger::error("Failed to load file: {}", filename);
```

```python
# Python example
from shared.libraries.core.logging.logger import Logger

logger = Logger(__name__)
logger.debug("Initializing component")
logger.error(f"Failed to load file: {filename}")
```

```typescript
// TypeScript example
import { Logger } from 'shared/libraries/core/logging/logger';

const logger = new Logger('ComponentName');
logger.debug('Initializing component');
logger.error(`Failed to load file: ${filename}`);
```

#### Configuration System
- Unified configuration management
- Environment-specific settings
- User preferences
- Default configurations

```cpp
// C++ example
#include "shared/libraries/core/config/config_manager.h"

auto& config = ConfigManager::getInstance();
std::string apiKey = config.getString("api.key");
int maxConnections = config.getInt("network.max_connections", 10);
```

```python
# Python example
from shared.libraries.core.config.config_manager import ConfigManager

config = ConfigManager.get_instance()
api_key = config.get_string("api.key")
max_connections = config.get_int("network.max_connections", 10)
```

```typescript
// TypeScript example
import { ConfigManager } from 'shared/libraries/core/config/config_manager';

const config = ConfigManager.getInstance();
const apiKey = config.getString('api.key');
const maxConnections = config.getInt('network.max_connections', 10);
```

### 2. UI Components

Shared UI components ensure a consistent look and feel across all RebelSUITE applications:

#### Theme System
- Light and dark themes
- Custom theme support
- Theme switching
- Accessibility considerations

```cpp
// C++ example
#include "shared/libraries/ui/theme/theme_manager.h"

auto& themeManager = ThemeManager::getInstance();
themeManager.setTheme("dark");
Color backgroundColor = themeManager.getColor("background");
```

```python
# Python example
from shared.libraries.ui.theme.theme_manager import ThemeManager

theme_manager = ThemeManager.get_instance()
theme_manager.set_theme("dark")
background_color = theme_manager.get_color("background")
```

```typescript
// TypeScript example
import { ThemeManager } from 'shared/libraries/ui/theme/theme_manager';

const themeManager = ThemeManager.getInstance();
themeManager.setTheme('dark');
const backgroundColor = themeManager.getColor('background');
```

#### Widget Library
- Common UI controls
- Dialogs and panels
- Layout managers
- Input handling

```cpp
// C++ example
#include "shared/libraries/ui/widgets/button.h"
#include "shared/libraries/ui/widgets/dialog.h"

auto button = std::make_shared<Button>("Save");
button->setOnClick([]() { saveFile(); });

Dialog dialog("Save File");
dialog.addWidget(button);
dialog.show();
```

```python
# Python example
from shared.libraries.ui.widgets.button import Button
from shared.libraries.ui.widgets.dialog import Dialog

button = Button("Save")
button.set_on_click(lambda: save_file())

dialog = Dialog("Save File")
dialog.add_widget(button)
dialog.show()
```

```typescript
// TypeScript example
import { Button } from 'shared/libraries/ui/widgets/button';
import { Dialog } from 'shared/libraries/ui/widgets/dialog';

const button = new Button('Save');
button.setOnClick(() => saveFile());

const dialog = new Dialog('Save File');
dialog.addWidget(button);
dialog.show();
```

### 3. File I/O Utilities

File I/O utilities provide consistent file handling across all components:

#### File System Operations
- File reading and writing
- Directory operations
- Path manipulation
- File watching

```cpp
// C++ example
#include "shared/libraries/io/file_system.h"

std::string content = FileSystem::readTextFile("config.json");
FileSystem::writeTextFile("output.txt", "Hello, world!");
bool exists = FileSystem::fileExists("data.bin");
```

```python
# Python example
from shared.libraries.io.file_system import FileSystem

content = FileSystem.read_text_file("config.json")
FileSystem.write_text_file("output.txt", "Hello, world!")
exists = FileSystem.file_exists("data.bin")
```

```typescript
// TypeScript example
import { FileSystem } from 'shared/libraries/io/file_system';

const content = FileSystem.readTextFile('config.json');
FileSystem.writeTextFile('output.txt', 'Hello, world!');
const exists = FileSystem.fileExists('data.bin');
```

#### Serialization
- JSON serialization
- Binary serialization
- XML serialization
- Custom format serialization

```cpp
// C++ example
#include "shared/libraries/io/serialization/json_serializer.h"

JsonObject config;
config["name"] = "RebelSUITE";
config["version"] = "1.0.0";
std::string json = JsonSerializer::serialize(config);
```

```python
# Python example
from shared.libraries.io.serialization.json_serializer import JsonSerializer

config = {
    "name": "RebelSUITE",
    "version": "1.0.0"
}
json = JsonSerializer.serialize(config)
```

```typescript
// TypeScript example
import { JsonSerializer } from 'shared/libraries/io/serialization/json_serializer';

const config = {
    name: 'RebelSUITE',
    version: '1.0.0'
};
const json = JsonSerializer.serialize(config);
```

### 4. Networking Utilities

Networking utilities facilitate communication between components:

#### IPC System
- Inter-process communication
- Message passing
- Remote procedure calls
- Event broadcasting

```cpp
// C++ example
#include "shared/libraries/network/ipc/ipc_client.h"

IpcClient client("RebelCAD");
client.connect();
client.sendMessage("RebelENGINE", "ImportModel", modelData);
```

```python
# Python example
from shared.libraries.network.ipc.ipc_client import IpcClient

client = IpcClient("RebelDESK")
client.connect()
client.send_message("RebelCODE", "ExecuteScript", script_data)
```

```typescript
// TypeScript example
import { IpcClient } from 'shared/libraries/network/ipc/ipc_client';

const client = new IpcClient('RebelFLOW');
client.connect();
client.sendMessage('RebelCAD', 'ExportModel', modelData);
```

#### HTTP Client
- REST API communication
- Authentication handling
- Request/response processing
- Error handling

```cpp
// C++ example
#include "shared/libraries/network/http/http_client.h"

HttpClient client;
HttpResponse response = client.get("https://api.example.com/data");
std::string data = response.getBody();
```

```python
# Python example
from shared.libraries.network.http.http_client import HttpClient

client = HttpClient()
response = client.get("https://api.example.com/data")
data = response.get_body()
```

```typescript
// TypeScript example
import { HttpClient } from 'shared/libraries/network/http/http_client';

const client = new HttpClient();
const response = await client.get('https://api.example.com/data');
const data = response.getBody();
```

## Shared Assets

### 1. Icons and Images

RebelSUITE uses a consistent set of icons across all components:

- **Action Icons**: Save, Open, Close, Delete, etc.
- **Tool Icons**: Select, Move, Rotate, Scale, etc.
- **Status Icons**: Success, Warning, Error, Info, etc.
- **File Type Icons**: Document, Image, Model, Script, etc.

Icons are available in multiple formats and resolutions:
- SVG for scalable icons
- PNG for raster icons (16x16, 24x24, 32x32, 48x48)
- Icon themes (light, dark, high contrast)

### 2. Fonts

RebelSUITE uses a consistent set of fonts across all components:

- **UI Font**: Inter (sans-serif)
- **Code Font**: JetBrains Mono (monospace)
- **Document Font**: Roboto (sans-serif)
- **Heading Font**: Montserrat (sans-serif)

Fonts are available in multiple weights and styles, and support a wide range of languages and characters.

### 3. Themes

RebelSUITE includes a set of predefined themes:

- **Light Theme**: Light background with dark text
- **Dark Theme**: Dark background with light text
- **High Contrast Theme**: Maximum contrast for accessibility
- **Blue Theme**: Blue-based color scheme
- **Green Theme**: Green-based color scheme

Themes define colors for:
- Background and foreground
- Primary and secondary colors
- Accent colors
- Status colors (success, warning, error, info)
- Text colors
- Border and shadow colors

## Shared File Formats

### 1. Model Formats

RebelSUITE uses common 3D model formats for exchange between components:

- **RebelModel (.rmodel)**: Native RebelSUITE model format
- **FBX (.fbx)**: Industry standard for 3D model exchange
- **glTF (.gltf, .glb)**: Modern 3D model format
- **OBJ (.obj)**: Simple 3D model format
- **STL (.stl)**: 3D printing format

### 2. Project Formats

RebelSUITE uses a common project format for sharing project data:

- **RebelProject (.rproj)**: Native RebelSUITE project format
- Project files include:
  - Project metadata
  - File references
  - Component-specific settings
  - Cross-component relationships

### 3. Workflow Formats

RebelSUITE uses a common workflow format for automation:

- **RebelFlow (.rflow)**: Native RebelSUITE workflow format
- Workflow files include:
  - Node definitions
  - Connection information
  - Execution settings
  - Input and output specifications

### 4. Script Formats

RebelSUITE supports multiple script formats:

- **Python (.py)**: For Python scripts
- **JavaScript (.js)**: For JavaScript scripts
- **TypeScript (.ts)**: For TypeScript scripts
- **Lua (.lua)**: For Lua scripts

## Shared Scripts

### 1. Build Scripts

Build scripts automate the build process for all components:

- **build_all.ps1**: Build all components
- **build_component.ps1**: Build a specific component
- **clean_build.ps1**: Clean build artifacts
- **generate_version.ps1**: Generate version information

### 2. Test Scripts

Test scripts automate testing for all components:

- **run_all_tests.ps1**: Run all tests
- **run_component_tests.ps1**: Run tests for a specific component
- **run_cross_tests.ps1**: Run cross-component tests
- **generate_test_report.ps1**: Generate test reports

### 3. Deployment Scripts

Deployment scripts automate the deployment process:

- **package_all.ps1**: Package all components
- **package_component.ps1**: Package a specific component
- **deploy_all.ps1**: Deploy all components
- **deploy_component.ps1**: Deploy a specific component

## Versioning and Compatibility

### 1. Version Numbering

RebelSUITE uses semantic versioning for all components:

- **Major Version**: Incompatible API changes
- **Minor Version**: Backwards-compatible new features
- **Patch Version**: Backwards-compatible bug fixes

Example: RebelSUITE 2.3.1

### 2. Compatibility Matrix

The compatibility matrix defines which versions of components work together:

| Component   | Version | Compatible With                                      |
|-------------|---------|------------------------------------------------------|
| RebelCAD    | 2.3.1   | RebelENGINE 2.x, RebelFLOW 2.x, RebelCODE 2.x        |
| RebelCODE   | 2.4.0   | RebelCAD 2.x, RebelENGINE 2.x, RebelFLOW 2.x         |
| RebelDESK   | 2.5.2   | RebelCAD 2.x, RebelCODE 2.x, RebelENGINE 2.x         |
| RebelENGINE | 2.2.3   | RebelCAD 2.x, RebelCODE 2.x, RebelFLOW 2.x           |
| RebelFLOW   | 2.1.0   | RebelCAD 2.x, RebelCODE 2.x, RebelENGINE 2.x         |

### 3. Backward Compatibility

RebelSUITE maintains backward compatibility within major versions:

- File formats are backward compatible within major versions
- APIs are backward compatible within major versions
- Plugins are backward compatible within major versions
- Scripts are backward compatible within major versions

## Conclusion

The shared resources and libraries in RebelSUITE provide a foundation for consistent, integrated development across all components. By leveraging these shared resources, developers can ensure that all components work together seamlessly while maintaining their ability to function independently.

For more information on specific shared resources, refer to the documentation in the shared/docs directory.
