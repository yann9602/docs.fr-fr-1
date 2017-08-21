---
title: "Guide pratique pour référencer un assembly avec un nom fort"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- strong-named assemblies, compile-time references
- compile-time assembly referencing
- assemblies [.NET Framework], strong-named
- assembly binding, strong-named
ms.assetid: 4c6a406a-b5eb-44fa-b4ed-4e95bb95a813
caps.latest.revision: 14
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: aa46bfdfe42dca9509e39d4b6218473aa00a1877
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-reference-a-strong-named-assembly"></a>Guide pratique pour référencer un assembly avec un nom fort
Le référencement de types ou de ressources dans un assembly avec nom fort est généralement un processus transparent. Vous pouvez effectuer la référence au moment de la compilation (liaison anticipée) ou au moment de l’exécution.  
  
 Une référence au moment de la compilation se produit quand vous indiquez au compilateur que votre assembly référence explicitement un autre assembly. Quand vous utilisez le référencement au moment de la compilation, le compilateur obtient automatiquement la clé publique de l’assembly avec nom fort ciblé et la place dans la référence d’assembly de l’assembly compilé.  
  
> [!NOTE]
>  Un assembly avec nom fort peut uniquement utiliser les types d'autres assemblys avec nom fort. Si ce n'était pas le cas, la sécurité de l'assembly avec nom fort serait compromise.  
  
### <a name="to-make-a-compile-time-reference-to-a-strong-named-assembly"></a>Pour effectuer une référence au moment de la compilation à un assembly avec nom fort  
  
1.  À l'invite de commandes, tapez la commande suivante :  
  
     \<*commande_compilateur*> **/reference:**\<*nom_assembly*>  
  
     Dans cette commande, *commande_compilateur* est la commande du compilateur pour le langage que vous utilisez, et *nom_assembly* est le nom de l’assembly avec nom fort référencé. Vous pouvez également utiliser d’autres options du compilateur, telles que **/t:library**, qui permet de créer un assembly de bibliothèque.  
  
 L’exemple suivant crée un assembly nommé `myAssembly.dll` qui référence un assembly avec nom fort nommé `myLibAssembly.dll` à partir d’un module de code nommé `myAssembly.cs`.  
  
```  
csc /t:library myAssembly.cs /reference:myLibAssembly.dll  
```  
  
### <a name="to-make-a-run-time-reference-to-a-strong-named-assembly"></a>Pour effectuer une référence au moment de l’exécution à un assembly avec nom fort  
  
1.  Quand vous effectuez une référence d’assembly avec nom fort au moment de l’exécution (par exemple, en utilisant la méthode <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName> ou <xref:System.Reflection.Assembly.GetType%2A?displayProperty=fullName>), vous devez utiliser le nom complet de l’assembly avec nom fort référencé. La syntaxe d’un nom complet est la suivante :  
  
     \<*nom_assembly*>**,** \<*numéro_version*>**,** \<*culture*>**,** \<*jeton_clé_publique*>  
  
     Exemple :  
  
    ```  
    myDll, Version=1.1.0.0, Culture=en, PublicKeyToken=03689116d3a4ae33   
    ```  
  
     Dans cet exemple, `PublicKeyToken` est la forme hexadécimale du jeton de clé publique. S’il n’existe aucune valeur de culture, utilisez `Culture=neutral`.  
  
 L’exemple de code suivant montre comment utiliser ces informations avec la méthode <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName>.  
  
 [!code-cpp[Assembly.Load1#3](../../../samples/snippets/cpp/VS_Snippets_CLR/Assembly.Load1/CPP/load2.cpp#3)] [!code-csharp[Assembly.Load1#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Assembly.Load1/CS/load2.cs#3)] [!code-vb[Assembly.Load1#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Assembly.Load1/VB/load2.vb#3)]  
  
 Vous pouvez imprimer le format hexadécimal de la clé publique et du jeton de clé publique pour un assembly spécifique en utilisant la commande [Strong Name (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) suivante :  
  
 **sn -Tp \<** *assembly* **>**  
  
 Si vous avez un fichier de clé publique, vous pouvez utiliser la commande suivante (notez la différence de casse de l’option de ligne de commande) à la place :  
  
 **sn -tp \<** *assembly* **>**  
  
## <a name="see-also"></a>Voir aussi  
 [Création et utilisation d’assemblys avec nom fort](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)

