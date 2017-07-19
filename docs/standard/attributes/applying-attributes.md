---
title: "Application des attributs | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "assemblys (.NET Framework), attributs"
  - "attributs (.NET Framework), appliquer"
ms.assetid: dd7604eb-9fa3-4b60-b2dd-b47739fa3148
caps.latest.revision: 19
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 19
---
# Application des attributs
Utilisez le processus suivant pour appliquer un attribut à un élément de votre code.  
  
1.  Définissez un nouvel attribut ou utilisez un attribut existant en important son espace de noms à partir du .NET Framework.  
  
2.  Appliquez l'attribut à l'élément de code en le plaçant immédiatement avant l'élément.  
  
     Chaque langage possède sa propre syntaxe d'attribut.  En C\+\+ et C\#, l'attribut est entouré de crochets et séparé de l'élément par un espace blanc qui peut inclure un saut de ligne.  En Visual Basic, l'attribut est entouré par des crochets angulaires et doit figurer sur la même ligne logique ; le caractère de continuation de ligne peut être utilisé si vous souhaitez un saut de ligne.  En J\#, l'attribut est attaché à l'aide d'une syntaxe de commentaire spéciale.  
  
3.  Spécifiez des paramètres positionnels et des paramètres nommés pour l'attribut.  
  
     Les paramètres positionnels sont obligatoires et doivent être placés avant tout paramètre nommé ; ils correspondent aux paramètres de l'un des constructeurs de l'attribut.  Les paramètres nommés sont facultatifs et correspondent aux propriétés en lecture\/écriture de l'attribut.  En C\+\+, C\# et J\#, spécifiez `name`\=`value`, où `name` est le nom de la propriété, pour chaque paramètre facultatif.  En Visual Basic, spécifiez `name`:\=`value`.  
  
 L'attribut est émis dans les métadonnées lorsque vous compilez votre code puis mis à disposition du Common Language Runtime et des applications ou outils personnalisés par l'intermédiaire des services de réflexion de l'exécution.  
  
 Par convention, tous les noms d'attributs se terminent par Attribute.  Cependant, plusieurs langages qui ciblent le runtime, tels que Visual Basic et C\#, n'exigent pas que vous spécifiiez le nom complet d'un attribut.  Par exemple, pour initialiser <xref:System.ObsoleteAttribute?displayProperty=fullName>, il vous suffit de le référencer en tant qu'**Obsolete**.  
  
## Application d'un attribut à une méthode  
 L'exemple de code suivant montre comment déclarer **System.ObsoleteAttribute**, qui marque le code comme étant obsolète.  La chaîne `"Will be removed in next version"` est passée à l'attribut.  Cet attribut provoque un avertissement du compilateur qui affiche la chaîne passée lorsque le code décrit par l'attribut est appelé.  
  
 [!code-cpp[Conceptual.Attributes.Usage#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source1.cpp#3)]
 [!code-csharp[Conceptual.Attributes.Usage#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source1.cs#3)]
 [!code-vb[Conceptual.Attributes.Usage#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source1.vb#3)]  
  
## Application des attributs au niveau de l'assembly  
 Si vous souhaitez appliquer un attribut au niveau de l'assembly, utilisez le mot clé **Assembly** \(`Assembly` dans Visual Basic\).  Le code suivant indique le **AssemblyTitleAttribute** appliqué au niveau de l'assembly.  
  
 [!code-cpp[Conceptual.Attributes.Usage#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source1.cpp#2)]
 [!code-csharp[Conceptual.Attributes.Usage#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source1.cs#2)]
 [!code-vb[Conceptual.Attributes.Usage#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source1.vb#2)]  
  
 Lorsque cet attribut est appliqué, la chaîne `"My Assembly"` est placée dans le manifeste d'assembly, dans la partie métadonnées du fichier.  Vous pouvez visualiser l'attribut en utilisant le [Désassembleur MSIL \(Ildasm.exe\)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) ou en créant un programme personnalisé pour récupérer l'attribut.  
  
## Voir aussi  
 [Attributs](../../../docs/standard/attributes/index.md)   
 [Récupération des informations stockées dans les attributs](../../../docs/standard/attributes/retrieving-information-stored-in-attributes.md)   
 [Concepts](../Topic/Attributed%20Programming%20Concepts.md)   
 [Attributs](../Topic/Attributes%20\(C%23%20and%20Visual%20Basic\).md)