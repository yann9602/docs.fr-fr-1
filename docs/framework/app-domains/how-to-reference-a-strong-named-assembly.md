---
title: "Comment&#160;: r&#233;f&#233;rencer un assembly avec nom fort | Microsoft Docs"
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
  - "assemblys (.NET Framework), dotés de nom fort"
  - "liaison d'assembly, dotés de nom fort"
  - "référencer des assemblys au moment de la compilation"
  - "assemblys avec nom fort, références au moment de la compilation"
ms.assetid: 4c6a406a-b5eb-44fa-b4ed-4e95bb95a813
caps.latest.revision: 14
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 14
---
# Comment&#160;: r&#233;f&#233;rencer un assembly avec nom fort
Le référencement de types ou de ressources dans un assembly avec nom fort est généralement un processus transparent.  Vous pouvez effectuer la référence au moment de la compilation \(liaison anticipée\) ou au moment de l'exécution.  
  
 Une référence au moment de la compilation se produit lorsque vous indiquez au compilateur que votre assembly référence explicitement un autre assembly.  Lorsque vous utilisez le référencement au moment de la compilation, le compilateur obtient automatiquement la clé publique de l'assembly avec nom fort cible et la place dans la référence d'assembly de l'assembly compilé.  
  
> [!NOTE]
>  Un assembly doté de nom fort peut uniquement utiliser les types d'autres assemblys dotés de noms forts.  Si ce n'était pas le cas, la sécurité de l'assembly doté de nom fort serait compromise.  
  
### Pour effectuer une référence au moment de la compilation à un assembly avec nom fort  
  
1.  À l'invite de commandes, tapez la commande suivante :  
  
     \<*compiler command*\> **\/reference:**\<*assembly name*\>  
  
     Dans cette commande, *compiler command* représente la commande du compilateur pour le langage utilisé et *assembly name* représente le nom de l'assembly avec nom fort référencé.  Vous pouvez également utiliser d'autres options du compilateur, telles que **\/t:library**, qui permet de créer un assembly de bibliothèque.  
  
 L'exemple suivant crée un assembly appelé `myAssembly.dll` qui référence un assembly avec nom fort appelé `myLibAssembly.dll`, à partir d'un module de code appelé `myAssembly.cs`.  
  
```  
csc /t:library myAssembly.cs /reference:myLibAssembly.dll  
```  
  
### Pour effectuer une référence au moment de l'exécution à un assembly avec nom fort  
  
1.  Lorsque vous effectuez une référence d'assembly avec nom fort au moment de l'exécution \(par exemple, en utilisant la méthode <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName> ou <xref:System.Reflection.Assembly.GetType%2A?displayProperty=fullName> \), vous devez utiliser le nom complet de l'assembly avec nom fort référencé.  La syntaxe d'un nom complet est la suivante :  
  
     \<*assembly name*\>**,** \<*version number*\>**,** \<*culture*\>**,** \<*public key token*\>  
  
     Par exemple :  
  
    ```  
    myDll, Version=1.1.0.0, Culture=en, PublicKeyToken=03689116d3a4ae33   
    ```  
  
     Dans cet exemple, `PublicKeyToken` est la forme hexadécimale du jeton de clé publique.  S'il n'y a aucune valeur de culture, utilisez `Culture=neutral`.  
  
 L'exemple de code suivant montre comment utiliser ces informations avec la méthode <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName>.  
  
 [!code-cpp[Assembly.Load1#3](../../../samples/snippets/cpp/VS_Snippets_CLR/Assembly.Load1/CPP/load2.cpp#3)]
 [!code-csharp[Assembly.Load1#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Assembly.Load1/CS/load2.cs#3)]
 [!code-vb[Assembly.Load1#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Assembly.Load1/VB/load2.vb#3)]  
  
 Vous pouvez imprimer le format hexadécimal de la clé publique et du jeton de clé publique pour un assembly spécifique en utilisant la commande [Nom fort \(Sn.exe\)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) suivante :  
  
 **sn \-Tp \<** *assembly* **\>**  
  
 Si vous avez un fichier de clé publique, vous pouvez également utiliser la commande suivante \(notez la différence de casse de l'option de ligne de commande\) :  
  
 **sn \-tp \<** *assembly* **\>**  
  
## Voir aussi  
 [Création et utilisation d'assemblys avec nom fort](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)