## Summary

Harden Claude AI integration and fix embedded Kafka test.

## What I changed

- Hardened external AI integration with timeouts and Resilience4j (retry + circuit-breaker).
- Added `ResilienceConfig` to log circuit-breaker state transitions for better observability.
- Configured `RestTemplate` timeouts in `ClaudeAiConfig`.
- Implemented fail-open-to-LOW behavior in `FraudDetectionService` when AI calls fail.
- Added `UserEventPublisher` Kafka producer and `UserEventPublisherEmbeddedTest` (embedded Kafka). Fixed producer key serializer and JSON Java time handling in tests.
- Updated `pom.xml` for annotation-processor ordering and Resilience4j dependencies.

## How to verify

1. Run unit tests locally:

```bash
mvn -B test
```

2. Run only the embedded Kafka test (optional):

```bash
mvn -Dtest=com.smartpay.userservice.event.UserEventPublisherEmbeddedTest test
```

## Checklist

- [ ] Code builds locally (`mvn -B test`)
- [ ] Relevant tests passing
- [ ] Add Resilience4j metrics via Micrometer
- [ ] Update CI to set `ANTHROPIC_API_KEY` secret

## Notes

- This environment cannot run `git`/`gh`; please run the branch and PR commands locally.
