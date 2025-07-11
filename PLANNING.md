# GitCraft Planning & Design Decisions

## Platform & Technology Stack

-   **Minecraft Version**: 1.16.5 (stable, extensive documentation)
-   **Mod Framework**: Forge (robust, large community)
-   **Target**: Client-side mod (users install locally)
-   **GitHub Integration**: Public repositories only (no authentication)

## World & Input Design

-   **World Type**: Custom "GitCraft" world type
-   **Repository Input**: GitHub URL entered during world creation
-   **World Characteristics**:
    -   Flat world with single repository visualization
    -   Read-only world (non-destructible)
    -   One repository per world

## Tree Visualization Architecture

### Coordinate System

-   **X, Y**: Branch positioning (horizontal plane)
-   **Z**: Commit sequence (vertical timeline)
-   **Main Branch**: Located at (0, 0) with commits extending in +Z direction

### Branch Representation

-   **Structure**: Wooden blocks forming branch "rails"
-   **Wood Types**: Map infinite git branches to finite wood types using modulo algorithm
-   **Positioning**: Each branch has unique (x, y) coordinates
-   **Spacing**: Adequate distance between branches for player navigation
-   **Merges**: Connected branches represent git merges

### Commit & File Visualization

-   **Commits**: Not represented by blocks, but by Z-coordinate positions
-   **Files**: Leaf blocks placed around wooden branch blocks at commit positions
-   **File Density**: Number of leaf blocks = dynamic based on file changes
-   **File Types**: Different leaf types mapped to file extensions (configurable)
-   **Spacing**: Strategic white-space for visual appeal

## Data Flow & Caching

-   **API Calls**: Fetch all repository data at world creation
-   **Caching**: Utilize Minecraft's built-in world save system
-   **Updates**:
    -   Automatic refresh on world startup
    -   Manual refresh option available
-   **Rate Limiting**: Handle GitHub API limits if necessary

## Core Classes Structure

```java
class GitBranch {
    String name;
    int x, y;  // position coordinates
    List<GitCommit> commits;
}

class GitCommit {
    String hash;
    int z;  // position on timeline
    List<GitFile> files;
}

class GitFile {
    String filename;
    String extension;
    int changeSize;  // affects leaf density
}
```

## Development Milestones

### MVP (Minimum Viable Product)

1. Custom GitCraft world type with URL input
2. GitHub API integration for main branch only
3. Simple wooden pillar representing main branch commits
4. Basic leaf placement for files

### Phase 2

1. Multi-branch support with proper positioning
2. Wood type mapping for different branches
3. File extension to leaf type mapping
4. Branch merge visualization

### Phase 3

1. Enhanced visual polish and spacing
2. Manual refresh functionality
3. Performance optimization
4. User configuration options

## Technical Considerations

-   **Project Structure**: Standard Forge mod layout
-   **Development Environment**: VSCode
-   **World Generation**: Custom dimension with controlled terrain
