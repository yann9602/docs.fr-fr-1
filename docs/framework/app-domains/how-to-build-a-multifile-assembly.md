---
title: "Comment&#160;: g&#233;n&#233;rer un assembly multifichier | Microsoft Docs"
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
  - "assemblys (.NET Framework), multifichiers"
  - "assembly (point d'entrée)"
  - "compiler des assemblys"
  - "Al.exe"
  - "compilateurs de ligne de commande"
  - "manifeste d’assembly, assemblys multifichiers"
  - "assemblys (.NET Framework), compiler"
  - "Assembly Linker"
  - "modules de code"
  - "assemblys multifichiers"
ms.assetid: 261c5583-8a76-412d-bda7-9b8ee3b131e5
caps.latest.revision: 15
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 15
---
# Comment&#160;: g&#233;n&#233;rer un assembly multifichier
Cet article explique comment créer un assembly multifichier et fournit le code illustrant chaque étape de la procédure.  
  
> [!NOTE]
>  L'IDE de Visual Studio pour C\# et Visual Basic ne peut être utilisé que pour créer des assemblys à fichier unique.  Si vous souhaitez créer des assemblys multifichiers, vous devez utiliser les compilateurs de ligne de commande ou Visual Studio avec Visual C\+\+.  
  
### Pour créer un assembly multifichier  
  
1.  Compilez tous les fichiers contenant des espaces de noms référencés par d'autres modules de l'assembly dans des modules de code.  L'extension par défaut pour les modules de code est .netmodule.  
  
     Par exemple, supposons que le fichier `Stringer` a un espace de noms appelé `myStringer`, qui inclut une classe appelée `Stringer`.  La classe `Stringer` contient une méthode appelée `StringerMethod` qui écrit une seule ligne dans la console.  
  
     [!code-cpp[Conceptual.Assembly.Multifile#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/stringer.cpp#1)]
     [!code-csharp[Conceptual.Assembly.Multifile#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/stringer.cs#1)]
     [!code-vb[Conceptual.Assembly.Multifile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/stringer.vb#1)]  
  
     Utilisez la commande suivante pour compiler ce code :  
  
     [!code-cpp[Conceptual.Assembly.Multifile#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/stringer.cpp#2)]
     [!code-csharp[Conceptual.Assembly.Multifile#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/stringer.cs#2)]
     [!code-vb[Conceptual.Assembly.Multifile#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/stringer.vb#2)]  
  
     La spécification du paramètre *module* à l'aide de l'option du compilateur **\/t:** indique que le fichier doit être compilé comme module et non pas comme assembly.  Le compilateur produit un module appelé `Stringer.netmodule`, qui peut être ajouté à un assembly.  
  
2.  Compilez tous les autres modules à l'aide des options du compilateur nécessaires pour indiquer les autres modules référencés dans le code.  Cette étape utilise l'option du compilateur **\/addmodule**.  
  
     Dans l'exemple suivant, un module de code appelé `Client` a une méthode `Main` de point d'entrée, qui référence une méthode du module `Stringer.dll` créé à l'étape 1.  
  
     [!code-cpp[Conceptual.Assembly.Multifile#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#3)]
     [!code-csharp[Conceptual.Assembly.Multifile#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#3)]
     [!code-vb[Conceptual.Assembly.Multifile#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#3)]  
  
     Utilisez la commande suivante pour compiler ce code :  
  
     [!code-cpp[Conceptual.Assembly.Multifile#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#4)]
     [!code-csharp[Conceptual.Assembly.Multifile#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#4)]
     [!code-vb[Conceptual.Assembly.Multifile#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#4)]  
  
     Spécifiez l'option **\/t:module** car ce module sera ajouté à un assembly dans une étape ultérieure.  Spécifiez l'option **\/addmodule** car le code de `Client` référence un espace de noms créé par le code dans `Stringer.netmodule`.  Le compilateur produit un module appelé `Client.netmodule` qui contient une référence à un autre module, `Stringer.netmodule`.  
  
    > [!NOTE]
    >  Les compilateurs C\# et Visual Basic prennent en charge la création directe d'assemblys multifichiers à l'aide de deux syntaxes différentes.  
    >   
    >  -   Deux compilations créent un assembly à deux fichiers :  
    >   
    >      [!code-cpp[Conceptual.Assembly.Multifile#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#5)]
      [!code-csharp[Conceptual.Assembly.Multifile#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#5)]
      [!code-vb[Conceptual.Assembly.Multifile#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#5)]  
    > -   Une compilation crée un assembly à deux fichiers :  
    >   
    >      [!code-cpp[Conceptual.Assembly.Multifile#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#6)]
      [!code-csharp[Conceptual.Assembly.Multifile#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#6)]
      [!code-vb[Conceptual.Assembly.Multifile#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#6)]  
  
3.  Utilisez l'utilitaire [Assembly Linker \(Al.exe\)](../../../docs/framework/tools/al-exe-assembly-linker.md) pour créer le fichier de sortie qui contient le manifeste d'assembly.  Ce fichier contient des informations sur les références de tous les modules ou ressources faisant partie de l'assembly.  
  
     À l'invite de commandes, tapez la commande suivante :  
  
     **al** \<*nom du module*\> \<*nom du module*\> … **\/main:**\<*nom de la méthode*\> **\/out:**\<*nom du fichier*\> **\/target:**\<*type du fichier d'assembly*\>  
  
     Dans cette commande, les arguments *nom du module* spécifient le nom de chaque module à inclure dans l'assembly.  L'option **\/main:** spécifie le nom de la méthode représentant le point d'entrée de l'assembly.  L'option **\/out:** spécifie le nom du fichier de sortie, qui contient les métadonnées de l'assembly.  L'option **\/target:** spécifie que l'assembly est un fichier exécutable \(.exe\) d'application console, un fichier exécutable Windows \(.win\) ou un fichier bibliothèque \(.lib\).  
  
     Dans l'exemple suivant, Al.exe crée un assembly qui est un exécutable d'application console appelé `myAssembly.exe`.  L'application se compose de deux modules appelés `Client.netmodule` et `Stringer.netmodule` et du fichier exécutable appelé `myAssembly.exe,` qui contient uniquement les métadonnées de l'assembly.  Le point d'entrée de l'assembly est la méthode `Main` de la classe `MainClientApp`, qui est située dans `Client.dll`.  
  
    ```  
    al Client.netmodule Stringer.netmodule /main:MainClientApp.Main /out:myAssembly.exe /target:exe   
    ```  
  
     Vous pouvez utiliser le [Désassembleur MSIL \(Ildasm.exe\)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) pour examiner le contenu d'un assembly ou déterminer si un fichier est un assembly ou un module.  
  
## Voir aussi  
 [Création d'assemblys](../../../docs/framework/app-domains/create-assemblies.md)   
 [Comment : afficher le contenu d'un assembly](../../../docs/framework/app-domains/how-to-view-assembly-contents.md)   
 [Méthode de localisation des assemblys par le runtime](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)   
 [Assemblys multifichiers](../../../docs/framework/app-domains/multifile-assemblies.md)