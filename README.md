# .NET Config :gear:

This action is responsible for installing the .NET SDK (or SDKs) on the workflow runner and add a custom NuGet source.

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

```yml
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
