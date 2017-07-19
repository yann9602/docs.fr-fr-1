---
title: "How to: Create COM Wrappers | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "COM,wrappers creating"
  - "COM,wrappers Visual Studio"
ms.assetid: bdf89bea-1623-45ee-a57b-cf7c90395efa
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# How to: Create COM Wrappers
Vous pouvez créer des wrappers COM \(Component Object Model\) à l'aide des fonctionnalités [!INCLUDE[vsprvsext](../../../includes/vsprvsext-md.md)] ou des outils .NET Framework Tlbimp.exe et Regasm.exe.  Ces deux méthodes génèrent deux types de wrappers COM :  
  
-   un [Runtime Callable Wrapper](../../../docs/framework/interop/runtime-callable-wrapper.md) d'une bibliothèque de types pour exécuter un objet COM en code managé ;  
  
-   un [COM Callable Wrapper](../../../docs/framework/interop/com-callable-wrapper.md) avec les paramètres de Registre requis pour exécuter un objet managé dans une application native.  
  
 Dans [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)], vous pouvez ajouter le wrapper COM à votre projet en tant que référence.  
  
## Encapsulation d'objets COM dans une application managée  
  
#### Pour créer un wrapper RCW \(Runtime Callable Wrapper\) à l'aide de Visual Studio  
  
1.  Ouvrez le projet pour votre application managée.  
  
2.  Dans le menu **Projet**, cliquez sur **Afficher tous les fichiers**.  
  
3.  Dans le menu **Projet**, cliquez sur **Ajouter une référence**.  
  
4.  Dans la boîte de dialogue Ajouter une référence, cliquez sur l'onglet **COM**, sélectionnez le composant que vous souhaitez utiliser et cliquez sur **OK**.  
  
     Dans l'**Explorateur de solutions**, notez que le composant COM est ajouté au dossier Références dans votre projet.  
  
 Vous pouvez maintenant écrire le code pour accéder à l'objet COM.  Vous pouvez commencer par déclarer l'objet, par exemple avec une instruction `Imports` pour [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] ou une instruction `Using` pour [!INCLUDE[csprcslong](../../../includes/csprcslong-md.md)].  
  
> [!NOTE]
>  Si vous souhaitez programmer des composants Microsoft Office, installez d'abord les [assemblys PIA \(Primary Interop Assembly\) de Microsoft Office](http://go.microsoft.com/fwlink/?LinkId=50479) à partir du Centre de téléchargement Microsoft.  À l'étape 4, sélectionnez la version la plus récente de la bibliothèque d'objets disponible pour le produit Office que vous souhaitez, comme la **Bibliothèque d'objets Microsoft Word 11.0** par exemple.  [](http://msdn.microsoft.com/fr-fr/c9d2a8b9-69df-4c0b-90ca-4d85bae063c4)  
  
#### Pour créer un wrapper RCW \(Runtime Callable Wrapper\) à l'aide d'outils .NET Framework  
  
-   Exécutez l'outil [Tlbimp.exe \(Type Library Importer\)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md).  
  
 Cet outil crée un assembly qui contient des métadonnées de runtime pour les types définis dans la bibliothèque de types d'origine.  
  
## Encapsulation d'objets managés dans une application native  
  
#### Pour créer un wrapper CCW \(COM Callable Wrapper\) à l'aide de Visual Studio  
  
1.  Créez un projet Bibliothèque de classes pour la classe managée que vous souhaitez exécuter en code natif.  La classe doit avoir un constructeur par défaut.  
  
     Vérifiez que vous disposez d'un numéro de version à quatre parties complet pour votre assembly dans le fichier AssemblyInfo.  Ce numéro est requis pour conserver le versioning dans le Registre Windows.  Pour plus d'informations sur les numéros de version, consultez [Versioning des assemblys](../../../docs/framework/app-domains/assembly-versioning.md).  
  
2.  Dans le menu **Projet**, cliquez sur **Propriétés**.  
  
3.  Cliquez sur l'onglet **Compiler**.  
  
4.  Activez la case à cocher **Inscrire pour COM Interop**.  
  
 Lorsque vous générez le projet, l'assembly est automatiquement inscrit pour COM Interop.  Si vous générez une application native dans [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)],  vous pouvez utiliser l'assembly en cliquant sur **Ajouter une référence** dans le menu **Projet**.  
  
#### Pour créer un wrapper CCW \(COM Callable Wrapper\) à l'aide d'outils .NET Framework  
  
-   Exécutez l'outil [Regasm.exe \(Assembly Registration Tool\)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md).  
  
 Cet outil lit les métadonnées de l'assembly et ajoute les entrées nécessaires au Registre.  Par conséquent, les clients COM peuvent créer des classes .NET Framework de manière transparente.  Vous pouvez utiliser l'assembly comme s'il s'agissait d'une classe COM native.  
  
 Vous pouvez exécuter Regasm.exe sur un assembly situé dans n'importe quel répertoire, puis exécuter l'[Gacutil.exe \(Global Assembly Cache Tool\)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) pour le déplacer dans le Global Assembly Cache.  Le déplacement de l'assembly n'invalide pas les entrées du Registre d'emplacement, car le Global Assembly Cache est toujours examiné si l'assembly est introuvable ailleurs.  
  
## Voir aussi  
 [Runtime Callable Wrapper](../../../docs/framework/interop/runtime-callable-wrapper.md)   
 [COM Callable Wrapper](../../../docs/framework/interop/com-callable-wrapper.md)