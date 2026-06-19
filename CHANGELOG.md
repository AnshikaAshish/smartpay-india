# Changelog

All notable changes to this repository will be documented in this file.

## [Unreleased]

- Harden Claude AI integration: timeouts, retry and circuit-breaker (Resilience4j).
- Add `ResilienceConfig` to log circuit-breaker state changes for observability.
- Provide `RestTemplate` configuration with sensible connect/read timeouts in `ClaudeAiConfig`.
- Implement fail-open-to-LOW behavior in `FraudDetectionService` when AI calls fail or time out.
- Add `UserEventPublisher` Kafka event publisher and `UserEventPublisherEmbeddedTest` (embedded Kafka integration test).
- Fix Embedded Kafka test: explicitly set producer key serializer to `StringSerializer` and register Java time modules for JSON mapping.
- Reordered annotation processors and added Resilience4j dependencies in `pom.xml`.

## Notes

- Run `mvn -B test` locally before creating the PR. I couldn't push or create the PR from this environment because `git` and `gh` are not available here.
