---
title: Ciblage de .NET Framework 2.0 sur Windows 8
description: "En savoir plus sur le ciblage d’une version antérieure du .NET Framework lors de l’utilisation de F #."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 63989543-95c3-4ab7-81f3-3834a8b15010
ms.openlocfilehash: 2c0191267da5bee7b844c11cdee168ccfb3321c4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="targeting-older-versions-of-net"></a>Ciblage des anciennes versions de .NET

> [!NOTE]
Cet article n’est pas à jour avec la dernière version de Visual Studio.  Il sera mis à jour.

L’erreur suivante peut s’afficher si vous tentez de cibler le .NET Framework 2.0, 3.0 ou 3.5 en F # de projet Visual Studio est installé sur Windows 8.1 : 

```
This project requires the 2.0 F# runtime, but that runtime is not installed.
```

Cette erreur est connue pour se produire dans la combinaison de conditions suivante :


- Vous avez installé Visual Studio sur Windows 8.1.
<br />

- Vous n’avez pas activé le .NET Framework 3.5 avant d’installer Visual Studio.
<br />

- Votre projet cible le .NET Framework 2.0, 3.0 ou 3.5.
<br />

Lorsque vous installez Visual Studio, il détecte les versions installées de .NET Framework et installe le Runtime F # 2.0 uniquement si le .NET Framework 3.5 est installé et activé.


## <a name="resolving-the-error"></a>Résoudre l’erreur
Pour résoudre cette erreur, vous pouvez soit une version plus récente du .NET Framework cible, ou vous pouvez activer le .NET Framework 3.5 sur Windows 8.1 et puis installez le runtime F # 2.0 en exécutant le programme d’installation de Visual Studio avec le **réparation** option.


#### <a name="to-enable-the-net-framework-35-on-windows-81"></a>Pour activer le .NET Framework 3.5 sur Windows 8.1

1. Sur le **Démarrer** écran, commencez à entrer **le panneau de configuration**.
<br />  Lorsque vous entrez ce nom, le **le panneau de configuration** icône s’affiche sous le **applications** titre.
<br />

2. Choisissez le **le panneau de configuration** icône, choisissez le **programmes** icône, puis choisissez le **ou désactiver des fonctionnalités Windows d’activer** lien.
<br />

3. Assurez-vous que le **.NET Framework 3.5 (inclut .NET 2.0 et 3.0)** case à cocher est sélectionnée, puis choisissez le **OK** bouton.
<br />  Vous n’avez pas besoin de sélectionner les cases à cocher pour tous les nœuds enfants pour les composants facultatifs du .NET Framework.
<br />  Le .NET Framework 3.5 est activée si elle n’était pas déjà.
<br />


#### <a name="to-install-the-f-20-runtime"></a>Pour installer le runtime F # 2.0

1. Dans le panneau de configuration, choisissez la **programmes** lier, puis choisissez le **programmes et fonctionnalités** lien.
<br />

2. Dans la liste des programmes installés, sélectionnez l’édition de Visual Studio que vous avez installé, puis choisissez le **modification** bouton.
<br />

3. Une fois que le programme d’installation démarre, choisissez le **réparation** bouton.
<br />  Pour plus d’informations, consultez [installation de Visual Studio](https://msdn.microsoft.com/library/e2h7fzkw.aspx).
<br />
## <a name="see-also"></a>Voir aussi
[Visual F#](../index.md)
