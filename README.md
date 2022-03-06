# The Debugging Flowchart!

## Version: 1.0.0

- [Changelog](./CHANGELOG.md)
- [License](./LICENSE)

Use this flowchart to navigate across debugging sessions.

## Contributing

This flowchart was created in [Excalidraw](https://excalidraw.com/). As the Excalidraw file emits JSON output, it can be easily versionable. Please submit your PRs updating the `.excalidraw` file and replacing the PNG (which you can export from Excalidraw itself).

You can also contribute by transalting the chart to other languages, creating new designs, you name it.

Don't forget to update the version, in the `.excalidraw` file, as well as the changelog and this file itself, as follows:

- **Patch**: Design tweaks, readability, color themes
- **Minor**: New flows or conventions
- **Major**: Flow updates, new flow remappings

---

Start here
---

```mermaid
flowchart TD
  subgraph NewFeature
    f-eg[Find example]
  end
  subgraph OnceWorked
    s-code[Search code]
  end
  0([Bug Reported!]) ==> feature?{New feature?}
  feature? -.No.-> worked?{Working before?}
  worked? --Yes--> OnceWorked
  worked? -.No.-> NewFeature
  feature? --Yes--> NewFeature
```

OnceWorked
---

```mermaid
flowchart TD
  subgraph AlignCode
    t-code[Try implement]
  end
  subgraph External
    ext-3rd{External/Third?}
  end
  subgraph Recheck
    all?{Exatly same?}
  end
  s-code[Search code] ==> code?{Same code?}
  code? --Yes--> s-data[Search data]
  code? -.No.-> AlignCode
  s-data ==> data?{Same data?}
  data? --Yes--> s-dep[Search dep]
  data? -.No.-> a-data[Align data]
  a-data ==> External
  s-dep ==> dep?{Same dep?}
  dep? --Yes--> s-env[Search env]
  dep? -.No.-> a-dep[Align dep]
  a-dep ==> External
  s-env ==> env?{Same env?}
  env? --Yes--> env#[ ]
  env? -.No.-> a-env[Align env]
  a-env ==> External
  env# ==> Recheck
```


NewFeature
---

```mermaid
flowchart TD
  subgraph OnceWorked
    code?{Same code?}
  end
  f-eg[Find example] --> local?{Local reference?}
  local? --Yes--> comp[Compare diff]
  local? -.No.-> remote?{Remote example?}
  comp ==> OnceWorked
  remote? --Yes--> bloker?{Block issue?}
  remote? -.No.-> 1((Escalate!))
  bloker? --Yes--> 1
  bloker? -.No.-> f-eg
```
