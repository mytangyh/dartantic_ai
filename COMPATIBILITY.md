# Flutter 3.27.4 compatibility

Branch: `compat/flutter-3.27.4` in `mytangyh/dartantic_ai`. Upstream baseline: `557f1584f26a302bbb00ac6d98df1f5e3e1de812` from csells/dartantic (formerly csells/dartantic_ai; the old URL redirects). FVM pins Flutter 3.27.4 / Dart 3.6.2 in this repository. Original package names, providers and licenses are retained.

The supported workspace contains dartantic_interface 3.0.0 and dartantic_ai 3.2.0. SDK constraints, collection/meta, test, lint and Melos versions match the old SDK; test_api's upstream forced override is removed. Source uses the Dart 3.6 formatter. Other samples and dartantic_chat remain present but unverified.

The public OpenAIResponsesEventMapper.containerId setter now accepts String? to match Dart 3.6 accessor type rules. Its getter remains nullable, and an explicit cast rejects null with TypeError before modifying state. This is a public static-signature widening, explained before implementation; valid assignments and dynamic-null rejection are preserved. No provider or feature was removed.

The root pubspec fixes the compatible AI clients, Google Cloud packages, SSE and GenUI core to full Git commit SHAs. The root lockfile records the same immutable sources; no temporary pubspec_overrides.yaml or local path dependency is needed. GenUI primitives/schema use its dedicated core checkpoint to avoid a dependency cycle with the final GenUI application commit.

2026-10-02: seven explicit secret-free upstream files passed, 146 tests including the accessor regression. Format checks pass for 199 source/test files; analysis has no errors or warnings and reports five infos, including intentional nullable-cast and dynamic-call coverage. GenUI's simple_chat unit tests (3), offline samples/mode tests (7, flutter-tester), and main Android APK build also pass.

GenUI provides `tool/compatibility/verify_dependency.ps1` with this offline profile. Live-provider tests remain separate and need real credentials; the mixed Anthropic file's two live requests failed in an initial list without credentials and were not changed or counted as passing. Real OpenAI-compatible streaming/history/tool execution passed through gpt-5.6-luna in Android simple_chat's three modes on Redmi 7A. Other live providers remain unverified; Windows is outside the user's final Android-only acceptance scope.
