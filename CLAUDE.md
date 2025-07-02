# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a simple Java Maven project demonstrating CI/CD workflows with GitHub Actions. The project builds a JAR file containing a HelloWorld application that prints the Java version.

## Development Commands

### Build Commands
- `mvn compile` - Compile the source code
- `mvn package` - Create JAR file in `target/` directory
- `mvn clean` - Remove generated files
- `mvn clean package` - Clean and build JAR file

### Run Commands
- `java -jar target/HelloWorld-1.0.0.jar` - Run the built JAR file
- `mvn exec:java` - Run the application directly via Maven

## Project Structure

```
src/main/java/com/example/
└── HelloWorld.java        # Main application class
```

## Key Configuration

### Maven Configuration (pom.xml)
- **Java Version**: 11 (source and target)
- **Main Class**: `com.example.HelloWorld`
- **Artifact**: `HelloWorld-1.0.0.jar`
- **Packaging**: JAR with manifest pointing to main class

### GitHub Actions Workflows

1. **mvn.yml** - Manual build and artifact upload
   - Triggered via workflow_dispatch
   - Builds with Java 17
   - Uploads JAR as GitHub artifact

2. **gh-release.yaml** - Automatic release on tag push
   - Triggered on git tags matching `v*`
   - Creates GitHub release with JAR attachment

3. **release-with-tag.yml** - Manual release with timestamp tags
   - Creates timestamp-based tags (format: `vYYYYMMDD-HHMM`)
   - Manual trigger via workflow_dispatch

## Architecture Notes

- Single-class application with no external dependencies
- JAR is configured as executable with main class manifest
- Uses exec-maven-plugin for direct execution
- No test framework currently configured

## Java Version Discrepancy

Note: The pom.xml specifies Java 11, but GitHub Actions workflows use Java 17. Consider aligning these versions for consistency.