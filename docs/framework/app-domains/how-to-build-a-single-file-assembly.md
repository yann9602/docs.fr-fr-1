---
title: "Comment&#160;: g&#233;n&#233;rer un assembly &#224; fichier unique | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-bcl"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "assemblys (.NET Framework), fichier unique"
  - "manifeste d'assembly, assemblys à fichier unique"
  - "modules de code"
  - "compilateurs de ligne de commande"
  - "assemblys de bibliothèque"
  - "nom du fichier de sortie pour les assemblys"
  - "assemblys à fichier unique"
ms.assetid: a6063221-43a5-4d3e-814c-288a4ec69aec
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# Comment&#160;: g&#233;n&#233;rer un assembly &#224; fichier unique
Un assembly à fichier unique, qui représente le type le plus simple d'assembly, contient des informations sur les types, l'implémentation, ainsi que le [manifeste d'assembly](../../../docs/framework/app-domains/assembly-manifest.md).  Vous pouvez utiliser des compilateurs de ligne de commande ou [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] pour créer un assembly à fichier unique.  Par défaut, le compilateur crée un fichier d'assembly avec une extension .exe.  
  
> [!NOTE]
>  [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] pour C\# et Visual Basic ne peut être utilisé que pour créer des assemblys à fichier unique.  Si vous souhaitez créer des assemblys multifichiers, vous devez utiliser les compilateurs de ligne de commande ou [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] pour Visual C\+\+.  
  
 Les procédures suivantes montrent comment créer des assemblys à fichier unique à l'aide de compilateurs de ligne de commande.  
  
### Pour créer un assembly avec une extension .exe  
  
1.  À l'invite de commandes, tapez la commande suivante :  
  
     \<*commande du compilateur*\> \<*nom du module*\>  
  
     Dans cette commande, *commande du compilateur* représente la commande du compilateur pour le langage utilisé dans votre module de code et *nom du module* représente le nom du module de code à compiler dans l'assembly.  
  
 L'exemple suivant crée un assembly appelé `myCode.exe` à partir d'un module de code appelé `myCode`.  
  
```csharp  
csc myCode.cs  
```  
  
```vb  
vbc myCode.vb  
```  
  
#### Pour créer un assembly avec une extension .exe et spécifier le nom du fichier de sortie  
  
1.  À l'invite de commandes, tapez la commande suivante :  
  
     \<*commande du compilateur*\> **\/out:**\<*nom du fichier*\> \<*nom du module*\>  
  
     Dans cette commande, *commande du compilateur* représente la commande du compilateur pour le langage utilisé dans votre module de code, *nom du fichier* représente le nom du fichier de sortie et *nom du module* représente le nom du module de code à compiler dans l'assembly.  
  
 L'exemple suivant crée un assembly appelé `myAssembly.exe` à partir d'un module de code appelé `myCode`.  
  
```csharp  
csc /out:myAssembly.exe myCode.cs  
```  
  
```vb  
vbc /out:myAssembly.exe myCode.vb  
```  
  
## Création d'assemblys de bibliothèque  
 Un assembly de bibliothèque ressemble à une bibliothèque de classes.  Il contient des types qui seront référencés par d'autres assemblys, mais ne possède aucun point d'entrée pour commencer l'exécution.  
  
#### Pour créer un assembly de bibliothèque  
  
1.  À l'invite de commandes, tapez la commande suivante :  
  
     \<*commande du compilateur*\> **\/t:library** \<*nom du module*\>  
  
     Dans cette commande, *commande du compilateur* représente la commande du compilateur pour le langage utilisé dans votre module de code et *nom du module* représente le nom du module de code à compiler dans l'assembly.  Vous pouvez également utiliser d'autres options du compilateur, telles que **\/out:**.  
  
 L'exemple suivant crée un assembly de bibliothèque appelé `myCodeAssembly.dll` à partir d'un module de code appelé `myCode`.  
  
```csharp  
csc /out:myCodeLibrary.dll /t:library myCode.cs  
```  
  
```vb  
vbc /out:myCodeLibrary.dll /t:library myCode.vb  
```  
  
## Voir aussi  
 [Création d'assemblys](../../../docs/framework/app-domains/create-assemblies.md)   
 [Assemblys multifichiers](../../../docs/framework/app-domains/multifile-assemblies.md)   
 [Comment : générer un assembly multifichier](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)   
 [Programmation à l'aide d'assemblys](../../../docs/framework/app-domains/programming-with-assemblies.md)