# KMP Promote Android App to Production

This GitHub Action automates the process of promoting an Android application from Beta to the Production track on the Google Play Store. It provides a streamlined workflow for handling production releases using Fastlane.

## Features

- Automated promotion to production track
- Secure handling of Play Store credentials
- Streamlined Fastlane configuration
- Minimal configuration requirements

## Prerequisites

- Android application already published on Play Store Beta
- Google Play Store developer account
- Play Store service account credentials
- Fastlane configuration in the repository

## Inputs

| Input                  | Description                                           | Required |
|------------------------|-------------------------------------------------------|----------|
| `playstore_creds`      | Base64 Encoded Firebase credentials JSON file content | Yes      |

## Usage

```yaml
jobs:
  promote-to-production:
    runs-on: macos-latest
    steps:
      - uses: openMF/kmp-publish-android-on-playstore-production-action@v2.0.0
        with:
          playstore_creds: ${{ secrets.PLAYSTORE_CREDS }}
```

## Workflow Details

1. **Environment Setup**
    - Configures Ruby environment
    - Sets up Fastlane with required plugins
    - Configures bundler for dependency management

2. **Credential Management**
    - Securely handles Play Store service account credentials
    - Creates credential file in the appropriate location

3. **Promotion Process**
    - Executes Fastlane command to promote the app to production
    - Uses existing Fastlane configuration from the repository

## Requirements

- GitHub Actions runner with Ubuntu
- Existing Fastlane configuration
- Play Store service account credentials
- Application must be in Beta track before promotion

## Notes

- This action only handles promotion to production
- Does not perform any building or signing operations
- Relies on existing app version in Beta track
- Uses Fastlane for Play Store interaction

## Security Considerations

- Play Store credentials should be stored as GitHub Secrets
- Credentials are handled securely and not exposed in logs
- Only minimal required permissions should be granted to service account

## Dependencies

- Ruby (installed via setup-ruby action)
- Bundler 2.2.27
- Fastlane with firebase_app_distribution plugin
- Fastlane with increment_build_number plugin
