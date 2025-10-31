# The Algorithms in Java

Collection of classic algorithms and data structures implemented in modern Java. The code is organized by topic (backtracking, bit manipulation, graph, dynamic programming, sorts, strings, trees, etc.) under the root package `com.thealgorithms` and is intended for educational use.

This project builds with Maven and targets Java 21.

## Repository layout

```
src/
	main/java/com/thealgorithms/
		backtracking/        # e.g., NQueens, KnightsTour, FloodFill
		bitmanipulation/     # e.g., HammingDistance, GrayCodeConversion
		...                  # many more categories
	test/java/com/thealgorithms/
		...                  # unit tests per category

pom.xml                  # Maven project configuration
checkstyle.xml           # Code style rules
spotbugs-exclude.xml     # SpotBugs suppressions
pmd-custom_ruleset.xml   # PMD rules
pmd-exclude.properties   # PMD suppressions
LICENSE                  # MIT License
```

## Prerequisites

- Java Development Kit (JDK) 21 or newer
- Apache Maven 3.9+

Check versions:

```
java -version
mvn -version
```

## Quick start

Build the project and run tests:

```
mvn clean test
```

Compile only:

```
mvn -q clean compile
```

Package the classes (outputs to `target/`):

```
mvn -q -DskipTests package
```

## Running an algorithm locally

Many classes include a `main` method for quick demos. After compiling/packaging, you can run such a class with the application classpath:

```
# Example: run a class that has a main method
mvn -q -DskipTests package
java -cp target/classes com.thealgorithms.backtracking.NQueens
```

If a class does not provide a `main` method, create a small driver in `src/main/java` or write a unit test in `src/test/java` to exercise it.

## Testing

Tests use JUnit Jupiter. Run the full test suite:

```
mvn test
```

Run a single test class or method:

```
# Class
mvn -Dtest=SomeClassTest test

# Method (ClassName#methodName)
mvn -Dtest=SomeClassTest#shouldComputeExpectedValue test
```

Generate a coverage report (JaCoCo):

```
mvn test jacoco:report
# Open target/site/jacoco/index.html in a browser
```

## Code quality and style

This repository includes static analysis and style checks. Run them locally:

```
# Checkstyle (code style)
mvn -q checkstyle:check

# PMD (code smells/rules)
mvn -q pmd:check

# SpotBugs (bug patterns; includes fb-contrib and FindSecBugs)
mvn -q spotbugs:check
```

Fix issues reported by these tools before submitting changes.

## Adding a new algorithm

1. Pick the appropriate package under `com.thealgorithms` or create a new one if necessary.
2. Implement the algorithm as a small, focused class with clear naming and Javadoc explaining the approach, complexity, and references if any.
3. Add unit tests under the mirrored package in `src/test/java` covering typical, edge, and error cases.
4. Ensure `mvn test`, Checkstyle, PMD, and SpotBugs pass locally.
5. Submit your change as a pull request with a concise description of the algorithm and citations if adapted from a source.

## Notes

- Implementations prioritize clarity for learning; they may not always be the most optimized version.
- Common helpers from Apache Commons (Lang and Collections) are available as dependencies where appropriate.

## License

This project is licensed under the MIT License. See `LICENSE` for details.
