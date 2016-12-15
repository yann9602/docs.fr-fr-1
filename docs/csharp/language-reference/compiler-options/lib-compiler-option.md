---
title: "/lib (C# Compiler Options) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/lib"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "lib compiler option [C#]"
  - "-lib compiler option [C#]"
  - "/lib compiler option [C#]"
ms.assetid: b0efcc88-e8aa-4df4-a00b-8bdef70b7673
caps.latest.revision: 16
caps.handback.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /lib (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

L'option **\/lib** spécifie l'emplacement des assemblys référencés à l'aide de l'option [\/reference \(Import Metadata\)](../../../csharp/language-reference/compiler-options/reference-compiler-option.md).  
  
## Syntaxe  
  
```  
/lib:dir1[,dir2]  
```  
  
## Arguments  
 `dir1`  
 Répertoire que le compilateur doit examiner si un assembly référencé est introuvable dans le répertoire de travail en cours \(répertoire à partir duquel vous appelez le compilateur\) ou dans le répertoire système du Common Language Runtime.  
  
 `dir2`  
 Tout autre répertoire supplémentaire dans lequel doivent être recherchées les références d'assembly.  Séparez les noms des répertoires supplémentaires par une virgule, sans espace entre eux.  
  
## Notes  
 Le compilateur recherche les références d'assembly qui ne sont pas complètement qualifiées dans l'ordre suivant :  
  
1.  Répertoire de travail en cours.  Il s'agit du répertoire à partir duquel le compilateur est appelé.  
  
2.  Répertoire système du Common Language Runtime.  
  
3.  Répertoires spécifiés par l'option **\/lib**.  
  
4.  Répertoires spécifiés par la variable d'environnement LIB.  
  
 Utilisez l'option **\/reference** pour spécifier une référence d'assembly.  
  
 L'option **\/lib** peut être spécifiée plusieurs fois ; chaque nouvelle valeur spécifiée est ajoutée à la valeur précédente.  
  
 Au lieu d'utiliser l'option **\/lib**, vous pouvez aussi copier tous les assemblys requis dans le répertoire de travail ; vous pourrez ainsi passer simplement le nom d'assembly à **\/reference**.  Vous pouvez ensuite supprimer les assemblys dans le répertoire de travail.  Dans la mesure où l'assembly dépendant n'est pas spécifié dans le manifeste d'assembly, vous pouvez démarrer l'application sur l'ordinateur cible, et trouver et utiliser l'assembly dans le Global Assembly Cache.  
  
 Que le compilateur puisse référencer l'assembly ne signifie pas que le Common Language Runtime est en mesure de trouver et charger l'assembly au moment de l'exécution.  Pour plus d'informations sur la manière dont le runtime recherche des assemblys référencés, consultez [Méthode de localisation des assemblys par le runtime](../Topic/How%20the%20Runtime%20Locates%20Assemblies.md).  
  
### Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriété** du projet.  
  
2.  Cliquez sur la page de propriétés **Chemin aux références**.  
  
3.  Modifiez le contenu de la zone de liste.  
  
 Pour plus d'informations sur la définition de cette option du compilateur par programme, consultez <xref:VSLangProj80.ProjectProperties3.ReferencePath%2A>.  
  
## Exemple  
 Compilez t2.cs pour créer un fichier .exe.  Le compilateur recherchera les références d'assembly dans le répertoire en cours et dans le répertoire racine du lecteur C.  
  
```  
csc /lib:c:\ /reference:t2.dll t2.cs  
```  
  
## Voir aussi  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [Comment : modifier des propriétés de projet et des paramètres de configuration](http://msdn.microsoft.com/fr-fr/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)