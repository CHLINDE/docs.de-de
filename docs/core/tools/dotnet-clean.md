---
title: dotnet clean-Befehl – .NET Core-CLI
description: Mit dem Befehl „dotnet clean“ wird das aktuelle Verzeichnis bereinigt.
author: mairaw
ms.author: mairaw
ms.date: 05/25/2018
ms.openlocfilehash: 9e68781fe00590f3c8d429631a3f72d525d29fa9
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34697030"
---
# <a name="dotnet-clean"></a>dotnet-clean

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>name

`dotnet clean`: Löscht die Ausgabe eines Projekts.

## <a name="synopsis"></a>Übersicht

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)
```
dotnet clean [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-r|--runtime] [-v|--verbosity]
dotnet clean [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)
```
dotnet clean [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-v|--verbosity]
dotnet clean [-h|--help]
```
---

## <a name="description"></a>description

Der Befehl `dotnet clean` löscht die Ausgabe des vorherigen Builds. Er ist als [MSBuild-Ziel](/visualstudio/msbuild/msbuild-targets) implementiert, sodass das Projekt ausgewertet wird, wenn der Befehl ausgeführt wird. Es werden nur die Ausgaben gelöscht, die während des Builds erstellt wurden. Sowohl der Ordner für Zwischenausgabe (*obj*) als auch der Ordner für die endgültige Ausgabe (*bin*) werden bereinigt.

## <a name="arguments"></a>Argumente

`PROJECT`

Das zu bereinigende MSBuild-Projekt. Wenn Sie keine Projektdatei angeben, durchsucht MSBuild das aktuelle Arbeitsverzeichnis nach einer Dateierweiterung, die mit *proj* endet, und verwendet diese.

## <a name="options"></a>Optionen

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

`-c|--configuration {Debug|Release}`

Legt die Buildkonfiguration fest. Der Standardwert ist `Debug`. Diese Option ist bei der Bereinigung nur erforderlich, wenn Sie sie bei der Erstellung angegeben haben.

`-f|--framework <FRAMEWORK>`

Das [Framework](../../standard/frameworks.md), das bei der Erstellung angegeben wurde. Das Framework muss in der [Projektdatei](csproj.md) definiert werden. Wenn Sie das Framework bei der Erstellung angegeben haben, müssen Sie das Framework bei der Bereinigung angeben.

`-h|--help`

Druckt eine kurze Hilfe für den Befehl.

`-o|--output <OUTPUT_DIRECTORY>`

Verzeichnis, in dem die Buildausgaben abgelegt wurden. Geben Sie den `-f|--framework <FRAMEWORK>`-Schalter mit dem Schalter des Ausgabeverzeichnisses an, wenn Sie das Framework bei der Erstellung des Projekts angegeben haben.

`-r|--runtime <RUNTIME_IDENTIFIER>`

Bereinigt den Ausgabeordner der angegebenen Runtime Wird bei der Erstellung einer [eigenständigen Bereitstellung](../deploying/index.md#self-contained-deployments-scd) verwendet.

`-v|--verbosity <LEVEL>`

Legt den Ausführlichkeitsgrad für den Befehl fest. Zulässige Grade sind q[uiet], m[inimal], n[ormal], d[etailed] und diag[nostic].

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

Legt die Buildkonfiguration fest. Der Standardwert ist `Debug`. Diese Option ist bei der Bereinigung nur erforderlich, wenn Sie sie bei der Erstellung angegeben haben.

`-f|--framework <FRAMEWORK>`

Das [Framework](../../standard/frameworks.md), das bei der Erstellung angegeben wurde. Das Framework muss in der [Projektdatei](csproj.md) definiert werden. Wenn Sie das Framework bei der Erstellung angegeben haben, müssen Sie das Framework bei der Bereinigung angeben.

`-h|--help`

Druckt eine kurze Hilfe für den Befehl.

`-o|--output <OUTPUT_DIRECTORY>`

Verzeichnis, in dem die Buildausgaben abgelegt wurden. Geben Sie den `-f|--framework <FRAMEWORK>`-Schalter mit dem Schalter des Ausgabeverzeichnisses an, wenn Sie das Framework bei der Erstellung des Projekts angegeben haben.

`-v|--verbosity <LEVEL>`

Legt den Ausführlichkeitsgrad für den Befehl fest. Zulässige Grade sind q[uiet], m[inimal], n[ormal], d[etailed] und diag[nostic].

---

## <a name="examples"></a>Beispiele

Bereinigen Sie einen Standardbuild des Projekts:

`dotnet clean`

Bereinigen Sie ein Projektbuild mit der Konfiguration „Release“:

`dotnet clean --configuration Release`
