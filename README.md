[![Playzor](https://raw.githubusercontent.com/fgilde/MudBlazor.Extensions/refs/heads/main/docs/playzor_logo.png)](https://playzor.net)

# Playzor

A Blazor playground you can host, embed or build on. Write a component, compile it with roslyn in
the browser, run it — no server round trip, no project, no install. Running instance:
[playzor.net](https://playzor.net).

| Package | What it is |
|---|---|
| [Playzor.Blazor.Editor](Playzor.Blazor.Editor/README.md) | The whole playground as one component: monaco, panels, tool bar |
| [Playzor.Core](Playzor.Core/README.md) | The compiler underneath, without any ui |
| [Playzor.Blazor](Playzor.Blazor/README.md) | The small embed — an iframe component and a web component |
| [Playzor.Server](Playzor.Server/README.md) | `MapPlayzorApi()`: nuget proxy and optional snippet endpoints |
| [Playzor.UserComponents](Playzor.UserComponents/README.md) | The stub assembly the compiled snippet replaces |

```csharp
builder.Services.AddPlayzor();
```

```razor
<PlayzorEditor Height="100%" />
```

## Building this repository

```bash
dotnet build Playzor.slnx
dotnet test Playzor.Tests/Playzor.Tests.csproj
```

The libraries depend on [MudBlazor.Extensions](https://github.com/fgilde/MudBlazor.Extensions),
and the reference follows your working copy: clone that repository **next to this one** and the
build compiles against its source, so a change spanning both is one build. Without it the published
package is used, which is what a build server always does.

```
github/
  MudBlazor.Extensions/
  Playzor/            <- you are here
```

`-p:UseMudExSource=true|false` overrides the choice.

## Releasing

Tag `playzor-v1.2.3`, or run the *Publish Playzor Packages* workflow with a version. All five
packages share one version, taken from the tag; `build/Playzor.props` holds the rest of the
metadata. Pushing uses NuGet trusted publishing, so there is no api key anywhere in this repository.

## License

MIT.
