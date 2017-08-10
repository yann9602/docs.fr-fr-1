---
title: Assemblys et le Global Assembly Cache (C#)
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 149f5ca5-5b34-4746-9542-1ae43b2d0256
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 2b98bd872bfdcbebb34fff3d878b92f39e27bbe0
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="assemblies-and-the-global-assembly-cache-c"></a>Assemblys et le Global Assembly Cache (C#)
Les assemblys constituent l’unité fondamentale dans le déploiement, la gestion de version, la portée d’activation et les autorisations de sécurité d’une application .NET. Les assemblys prennent la forme d’un fichier exécutable (.exe) ou d’un fichier de bibliothèque de liens dynamiques (.dll) et sont les blocs de construction du .NET Framework. Ils fournissent au Common Language Runtime les informations dont il a besoin pour connaître les implémentations de type. Vous pouvez comparer un assembly à une collection de types et de ressources conçus pour opérer ensemble et former une unité logique de fonctionnalité.  
  
 Les assemblys peuvent contenir un ou plusieurs modules. Par exemple, les projets plus importants peuvent être planifiés de sorte que plusieurs développeurs individuels travaillent sur des modules distincts, qui se regroupent pour créer un assembly unique. Pour plus d’informations sur les modules, consultez la rubrique [Comment : générer un assembly multifichier](https://msdn.microsoft.com/library/226t7yxe).  
  
 Les assemblys ont les propriétés suivantes :  
  
-   Les assemblys sont implémentés en tant que fichiers .exe ou .dll.  
  
-   Vous pouvez partager un assembly entre des applications en le plaçant dans le Global Assembly Cache. Les assemblys doivent avoir un nom fort avant d’être inclus dans le GAC. Pour plus d’informations, consultez [Assemblys avec nom fort](https://msdn.microsoft.com/library/wd40t7ad).  
  
-   Les assemblys sont chargés en mémoire uniquement s’ils sont requis. S’ils ne sont pas utilisés, ils ne sont pas chargés. Cela signifie que les assemblys peuvent être un moyen efficace pour gérer les ressources dans les grands projets.  
  
-   Vous pouvez obtenir par programme des informations sur un assembly à l’aide de la réflexion. Pour plus d’informations, consultez [Réflexion (C#)](../../../../csharp/programming-guide/concepts/reflection.md).  
  
-   Si vous voulez charger un assembly seulement pour l’inspecter, utilisez une méthode comme <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A>.  
  
## <a name="assembly-manifest"></a>Manifeste d'assembly  
 Tous les assemblys contiennent un *manifeste d’assembly*. Semblable à une table des matières, le manifeste d’assembly contient les éléments suivants :  
  
-   L’identité de l’assembly (nom et version).  
  
-   Une table de fichiers décrivant tous les autres fichiers qui composent l’assembly, par exemple, les autres assemblys que vous avez créés et qui sont utilisés par votre fichier .exe ou .dll, ou même des fichiers bitmap ou Readme.  
  
-   Une *liste de référence de l’assembly*, qui est une liste de toutes les dépendances externes, fichiers .dll ou autres, nécessaires à votre application qui ont été créés par quelqu’un d’autre. Les références de l’assembly contiennent des références aux objets globaux et privés. Les objets globaux se trouvent dans le Global Assembly Cache, une zone disponible pour d’autres applications. Les objets privés doivent être dans un répertoire au même niveau ou à un niveau inférieur que celui du répertoire dans lequel votre application est installée.  
  
 Comme les assemblys contiennent des informations sur le contenu, le contrôle de version et les dépendances, les applications créées avec C# ne dépendent pas des valeurs du Registre Windows pour fonctionner correctement. Les assemblys réduisent les conflits de fichiers .dll et rendent vos applications plus fiables et plus faciles à déployer. Dans de nombreux cas, vous pouvez installer une application .NET simplement en copiant ses fichiers sur l’ordinateur cible.  
  
 Pour plus d’informations, consultez [Manifeste d’assembly](https://msdn.microsoft.com/library/1w45z383).  
  
## <a name="adding-a-reference-to-an-assembly"></a>Ajout d’une référence à un assembly  
 Pour utiliser un assembly, vous devez y ajouter une référence. Ensuite, vous utilisez [la directive using](../../../../csharp/language-reference/keywords/using-directive.md) pour choisir l’espace de noms des éléments que vous voulez utiliser. Une fois qu’un assembly est référencé et importé, toutes les classes, propriétés, méthodes accessibles et les autres membres de ses espaces de noms sont disponibles pour votre application comme si leur code faisait partie de votre fichier source.  
  
 En C#, vous pouvez aussi utiliser deux versions du même assembly dans une même application. Pour plus d’informations, consultez [extern alias](../../../../csharp/language-reference/keywords/extern-alias.md).  
  
## <a name="creating-an-assembly"></a>Création d’un assembly  
 Compilez votre application en cliquant sur **Générer** dans le menu **Générer** ou en la générant à partir de la ligne de commande avec le compilateur en ligne de commande. Pour plus d’informations sur la génération d’assemblys à partir de la ligne de commande, consultez [Génération à partir de la ligne de commande avec csc.exe](../../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).  
  
> [!NOTE]
>  Pour générer un assembly dans Visual Studio, dans le menu **Générer**, choisissez **Générer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../../csharp/programming-guide/index.md)   
 [Assemblys dans le common language runtime](https://msdn.microsoft.com/library/k3677y81)   
 [Assemblys friend (C++)](friend-assemblies.md)   
 [Guide pratique pour partager un assembly avec d’autres applications (C#)](how-to-share-an-assembly-with-other-applications.md)   
 [Guide pratique pour charger et décharger des assemblys (C#)](how-to-load-and-unload-assemblies.md)   
 [Guide pratique pour déterminer si un fichier est un assembly (C#)](how-to-determine-if-a-file-is-an-assembly.md)   
 [Guide pratique pour créer et utiliser des assemblys à l’aide de la ligne de commande (C#)](how-to-create-and-use-assemblies-using-the-command-line.md)   
 [Procédure pas à pas : incorporation de types provenant d’assemblys managés dans Visual Studio (C#)](walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md)   
 [Procédure pas à pas : incorporation d’informations de type provenant d’assemblys Microsoft Office dans Visual Studio (C#)](walkthrough-embedding-type-information-from-microsoft-office-assemblies.md)

