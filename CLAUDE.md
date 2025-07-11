# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

GitCraft is a Minecraft Forge 1.16.5 client-side mod that transforms GitHub repositories into living, interactive trees within a custom GitCraft dimension. Project planning is complete - ready for implementation phase.

## Technical Specifications

**Platform**: Minecraft Forge 1.16.5 client-side mod
**Integration**: GitHub public repositories only
**World Type**: Custom GitCraft dimension (flat, read-only)
**Visualization**: Network graph approach with Z-axis timeline

### Architecture Overview

-   **Branches**: Wooden blocks at unique (x,y) coordinates
-   **Commits**: Z-axis positions with leaf blocks for files
-   **Files**: Leaf density based on file changes, types mapped to leaf variants
-   **Input**: GitHub URL entered during world creation
-   **Updates**: World startup + manual refresh option

## Repository Status

-   **Current State**: Planning complete, ready for implementation
-   **Files**: README.md, CLAUDE.md, PLANNING.md
-   **Next Phase**: MVP development (main branch visualization)

## Development Environment Setup

When implementing:

1. Use IntelliJ IDEA with Forge MDK template
2. Target Minecraft 1.16.5 with Forge
3. GitHub API integration for repository data
4. Custom world generation for GitCraft dimension

## Core Classes Structure

```java
GitBranch { String name; int x,y; List<GitCommit> commits; }
GitCommit { String hash; int z; List<GitFile> files; }
GitFile { String filename; String extension; int changeSize; }
```

*Note: Keep updating CLAUDE.md and README.md after each task and ask to commit and push changes*
