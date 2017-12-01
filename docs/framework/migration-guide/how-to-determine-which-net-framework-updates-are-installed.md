---
title: "Comment : déterminer les mises à jour de sécurité .NET Framework et les correctifs logiciels sont installés."
description: "Découvrez comment déterminer les correctifs logiciels et les mises à jour de sécurité .NET Framework sont installées sur un ordinateur."
ms.date: 11/21/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- updates, determining for .NET Framework
- .NET Framework, determining updates
ms.assetid: 53c7b5f7-d47a-402a-b194-7244a696a88b
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c35705470a8e1b553eca2ca0c68d3b8b9b3f6fa6
ms.sourcegitcommit: a3ba258f7a8cab5c6d19a3743dd95e904ecebc44
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2017
---
# <a name="how-to-determine-which-net-framework-security-updates-and-hotfixes-are-installed"></a>Comment : déterminer les mises à jour de sécurité .NET Framework et les correctifs logiciels sont installés.

Cet article vous explique comment rechercher des mises à jour de sécurité du .NET Framework et les correctifs logiciels sont installés sur un ordinateur.

> [!NOTE]
> Toutes les techniques indiqués dans cet article nécessitent un compte avec des privilèges d’administrateur.

## <a name="to-find-installed-updates-using-the-registry"></a>Pour rechercher installé les mises à jour à l’aide du Registre

Les mises à jour de sécurité installées et les correctifs logiciels pour chaque version du .NET Framework sont installées sur un ordinateur sont répertoriés dans le Registre Windows. Vous pouvez utiliser l’Éditeur du Registre (*regedit.exe*) programme pour afficher ces informations.

1. Ouvrez le programme **regedit.exe**. Dans Windows 8 et versions ultérieures, cliquez sur **Démarrer** ![logo Windows](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo"), puis sélectionnez **exécuter**. Dans le **ouvrir** , entrez **regedit** et sélectionnez **OK**.

2. Dans l'Éditeur du Registre, ouvrez la sous-clé suivante :

     `HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates`

     Les mises à jour installées sont répertoriées sous les sous-clés qui identifient la version du .NET Framework auquel elles s'appliquent. Chaque mise à jour est identifiée par un numéro de Base de connaissances (KB).

Dans l'Éditeur du Registre, les versions du .NET Framework et les mises à jour installées pour chaque version sont stockées dans des sous-clés distinctes. Pour plus d’informations sur la détection des numéros des versions installées, consultez [Comment : déterminer les versions de .NET Framework sont installées](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md).

## <a name="to-find-installed-updates-by-querying-the-registry-in-code"></a>Pour rechercher les mises à jour installées en interrogeant le Registre dans le code

L’exemple suivant détermine par programmation les mises à jour de sécurité .NET Framework et les correctifs logiciels qui sont installés sur un ordinateur :

[!code-csharp[ListUpdates](../../../samples/snippets/csharp/VS_Snippets_CLR/listupdates/cs/program.cs)]
[!code-vb[ListUpdates](../../../samples/snippets/visualbasic/VS_Snippets_CLR/listupdates/vb/program.vb)]

Cet exemple produit une sortie semblable à la suivante :

```console
Microsoft .NET Framework 4 Client Profile
  KB2468871
  KB2468871v2
  KB2478063
  KB2533523
  KB2544514
  KB2600211
  KB2600217
Microsoft .NET Framework 4 Extended
  KB2468871
  KB2468871v2
  KB2478063
  KB2533523
  KB2544514
  KB2600211
  KB2600217
```

## <a name="to-find-installed-updates-by-querying-the-registry-in-powershell"></a>Pour rechercher les mises à jour installées en interrogeant le Registre dans PowerShell

L’exemple suivant montre comment déterminer les mises à jour de sécurité .NET Framework et les correctifs logiciels qui sont installés sur un ordinateur à l’aide de PowerShell :

```powershell
 Get-ChildItem "HKLM:SOFTWARE\Wow6432Node\Microsoft\Updates\*" -Recurse | Where-Object {$_.name -like
 "*.NET Framework*"}
```

Cet exemple produit une sortie semblable à la suivante :

```console
    Hive: HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates\Microsoft .NET Framework 4 Client Profile


Name                           Property
----                           --------
KB2468871                      ThisVersionInstalled : Y
KB2468871v2                    ThisVersionInstalled : Y
KB2478063                      ThisVersionInstalled : Y
KB2533523                      ThisVersionInstalled : Y
KB2544514                      ThisVersionInstalled : Y
KB2600211                      ThisVersionInstalled : Y
KB2600217                      ThisVersionInstalled : Y


    Hive: HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates\Microsoft .NET Framework 4 Extended


Name                           Property
----                           --------
KB2468871                      ThisVersionInstalled : Y
KB2468871v2                    ThisVersionInstalled : Y
KB2478063                      ThisVersionInstalled : Y
KB2533523                      ThisVersionInstalled : Y
KB2544514                      ThisVersionInstalled : Y
KB2600211                      ThisVersionInstalled : Y
KB2600217                      ThisVersionInstalled : Y
```

## <a name="see-also"></a>Voir aussi

[Comment : déterminer les versions de .NET Framework sont installées](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)  
[Installer le .NET Framework pour les développeurs](../../../docs/framework/install/guide-for-developers.md)  
[Versions et dépendances](../../../docs/framework/migration-guide/versions-and-dependencies.md)
