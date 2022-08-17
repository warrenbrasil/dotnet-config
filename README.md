| [Main](../README.md) > .NET Config |
| ---------------------------------- |

# .NET Config :gear:

This action is responsible for installing the .NET SDK on the workflow runner and add the Warren GitHub Packages NuGet source. The SDK (or SDKs)

## Inputs

### `dotnet-version`

**Required**: The SDK version (or versions) to be installed

### `nuget-user`

**Required**: User that will read/write packages

### `nuget-api-key`

**Required**: The API key to authorize read/write packages

### `nuget-source`

**Required**: The URL to NuGet source index.json

### `nuget-source-name`

**Required**: The source name to be saved in nuget.config file

## Usage

Use `actions/checkout@v3` to clone this repository from your workflow run. You only need to checkout your repository and `dotnet actions` repository **ONCE** per job.

```yml
# Clone your repository
- name: Checkout Repository
  uses: actions/checkout@v3
  with:
    fetch-depth: 0

# Clone the actions repository
- name: Checkout dotnet-actions
  uses: actions/checkout@v3
  with:
    fetch-depth: 0
    repository: warrenbrasil/dotnet-actions
    token: ${{ secrets.WARRENBRASIL_GITHUB_PAT }}
    path: .github/actions

# Install the .NET SDK and configure Warren GitHub Packages Source
- name: Configure .NET
  uses: ./.github/actions/dotnet-config
  with:
    dotnet-version: 6.0.x
    nuget-user: ${{ secrets.NUGET_USER }}
    nuget-api-key: ${{ secrets.NUGETAPIKEY }}
    nuget-source: ${{ secrets.NUGET_SOURCE }}
    nuget-source-name: ${{ secrets.NUGET_SOURCE_NAME }}
```

Installing multiple .NET SDKs:

```yml
# Clone your repository
- name: Checkout Repository
  uses: actions/checkout@v3
  with:
    fetch-depth: 0

# Clone the actions repository
- name: Checkout dotnet-actions
  uses: actions/checkout@v3
  with:
    fetch-depth: 0
    repository: warrenbrasil/dotnet-actions
    token: ${{ secrets.WARRENBRASIL_GITHUB_PAT }}
    path: .github/actions

# Install the .NET SDKs and configure Warren GitHub Packages Source
- name: Configure .NET
  uses: ./.github/actions/dotnet-config
  with:
    dotnet-version: |
      6.0.x
      3.1.x
    nuget-user: ${{ secrets.NUGET_USER }}
    nuget-api-key: ${{ secrets.NUGETAPIKEY }}
    nuget-source: ${{ secrets.NUGET_SOURCE }}
    nuget-source-name: ${{ secrets.NUGET_SOURCE_NAME }}
```

<br>
<br>

| [Go Back](../README.md) |
| ----------------------- |
