---
title: "/reference (C# Compiler Options) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/reference"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/r compiler option [C#]"
  - "reference compiler option [C#]"
  - "r compiler option [C#]"
  - "/reference compiler option [C#]"
  - "-r compiler option [C#]"
  - "metadata import [C#]"
  - "public type information [C#]"
  - "-reference compiler option [C#]"
ms.assetid: 8d13e5b0-abf6-4c46-bf71-2daf2cd0a6c4
caps.latest.revision: 28
caps.handback.revision: 28
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /reference (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

L'option **\/reference** fait en sorte que le compilateur importe des informations de type [public](../../../csharp/language-reference/keywords/public.md) dans le fichier spécifié dans le projet actuel, vous permettant ainsi de référencer les métadonnées provenant des fichiers d'assembly spécifiés.  
  
## Syntaxe  
  
```  
/reference:[alias=]filename  
/reference:filename  
```  
  
## Arguments  
 `filename`  
 Nom d'un fichier comportant un manifeste d'assembly.  Pour importer plusieurs fichiers, incluez une option **\/reference** distincte pour chaque fichier.  
  
 `alias`  
 Identificateur C\# valide représentant un espace de noms racine qui contiendra tous les espaces de noms de l'assembly.  
  
## Notes  
 Pour effectuer une importation à partir de plusieurs fichiers, incluez une option **\/reference** distincte pour chaque fichier.  
  
 Les fichiers que vous importez doivent contenir un manifeste ; le fichier de sortie doit avoir été compilé à l'aide d'une option [\/target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) différente de [\/target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md).  
  
 **\/r** est la forme abrégée de **\/reference**.  
  
 Utilisez [\/addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md) pour importer des métadonnées à partir d'un fichier de sortie qui ne contient pas de manifeste d'assembly.  
  
 Si vous référencez un assembly \(assembly A\) qui lui\-même référence un autre assembly \(assembly B\), vous devrez référencer l'assembly B dans les cas suivants :  
  
-   Un type que vous utilisez à partir de l'Assembly A hérite d'un type ou implémente une interface à partir de l'Assembly B.  
  
-   Vous appelez un champ, une propriété, un événement ou une méthode dont le type de retour ou de paramètre est issu de l'assembly B.  
  
 Utilisez l'option [\/lib](../../../csharp/language-reference/compiler-options/lib-compiler-option.md) pour spécifier le répertoire dans lequel se trouvent une ou plusieurs de vos références d'assembly.  La rubrique **\/lib** indique également les répertoires dans lesquels le compilateur recherche les assemblys.  
  
 Pour que le compilateur reconnaisse un type dans un assembly \(et non un module\), il doit être forcé à résoudre le type. Pour ce faire, vous pouvez définir une instance du type.  Le compilateur peut résoudre les noms de types d'un assembly de plusieurs autres façons : par exemple, lorsqu'un type est hérité d'un autre type d'un assembly, le nom du type est alors reconnu par le compilateur.  
  
 Il est parfois nécessaire de référencer deux versions différentes du même composant dans un même assembly.  Pour ce faire, utilisez la sous\-option d'alias du commutateur **\/reference** pour chaque fichier, afin d'établir une distinction entre les deux fichiers.  Cet alias sera utilisé comme qualificateur pour le nom de composant et mettra en correspondance le composant avec l'un des fichiers.  
  
 Le fichier réponse \(.rsp\) csc, qui fait référence aux assemblys .NET Framework couramment utilisés, est utilisé par défaut.  Utilisez [\/noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md) si vous ne souhaitez pas que le compilateur utilise le fichier csc.rsp.  
  
> [!NOTE]
>  Dans Visual Studio, utilisez la boîte de dialogue **Ajouter une référence**.  Pour plus d'informations, consultez [Comment : ajouter ou supprimer des références à l'aide de la boîte de dialogue Ajouter une référence](http://msdn.microsoft.com/fr-fr/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  Dans Visual Studio 2010 et les versions ultérieures, afin de garantir un comportement équivalent entre l'ajout de références à l'aide de `/reference` et à l'aide de la boîte de dialogue **Ajouter une référence**, la propriété **Incorporer les types d'interopérabilité** doit être définie sur **False** pour l'assembly que vous ajoutez.  **True** est la valeur par défaut de cette propriété.  
  
## Exemple  
 Cet exemple montre comment utiliser la fonctionnalité [alias extern](../../../csharp/language-reference/keywords/extern-alias.md) \(page éventuellement en anglais\).  
  
 Vous compilez le fichier source et importez les métadonnées à partir des fichiers `grid.dll` et `grid20.dll`,  `` , qui ont été compilées précédemment.  Les deux DLL contiennent des versions séparées du même composant, et vous utilisez deux **\/reference** avec des options d'alias pour compiler le fichier source.  Les options se présentent comme suit :  
  
 \/reference:GridV1\=grid.dll and \/reference:GridV2\=grid20.dll  
  
 Ceci permet de configurer les alias externes "GridV1" et "GridV2" que vous utilisez dans votre programme au moyen d'une instruction extern :  
  
```  
extern alias GridV1;  
extern alias GridV2;  
// Using statements go here.  
```  
  
 Une fois que vous avez terminé, vous pouvez faire référence au contrôle grid à partir de grid.dll, en faisant précéder le nom du contrôle du préfixe GridV1, comme indiqué ci\-dessous :  
  
```  
GridV1::Grid  
```  
  
 De plus, vous pouvez faire référence au contrôle grid à partir de grid20.dll en faisant précéder le nom du contrôle du préfixe GridV2, comme indiqué ci\-dessous :  
  
```  
GridV2::Grid   
```  
  
## Voir aussi  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [Comment : modifier des propriétés de projet et des paramètres de configuration](http://msdn.microsoft.com/fr-fr/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)