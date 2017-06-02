---
title: "Temporisation de signature d&#39;un assembly | Microsoft Docs"
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
  - "reporter la signature d'assembly"
  - "signer des assemblys"
  - "assemblys (.NET Framework), signature"
  - "assemblys avec nom fort, temporisation de la signature d’assembly"
  - "signature d'assembly partielle"
ms.assetid: 9d300e17-5bf1-4360-97da-2aa55efd9070
caps.latest.revision: 15
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 15
---
# Temporisation de signature d&#39;un assembly
Une société peut conserver sous protection une paire de clés à laquelle les développeurs n'ont pas accès quotidiennement.  La clé publique est souvent disponible, mais l'accès à la clé privée est limité à quelques personnes.  Lors du développement d'assemblys avec des noms forts, chaque assembly qui référence l'assembly avec nom fort cible contient le jeton de la clé publique utilisée pour affecter un nom fort à l'assembly cible.  La clé publique doit donc être disponible pendant le processus de développement.  
  
 Vous pouvez utiliser la signature temporisée ou partielle au moment de la génération pour réserver de l'espace dans le fichier exécutable portable \(PE\) pour la signature de nom fort, mais différer la signature réelle à une étape ultérieure \(généralement juste avant de livrer l'assembly\).  
  
 Les étapes suivantes mettent en avant le processus de temporisation de la signature d'un assembly :  
  
1.  Obtenez la clé publique de la paire de clés de la société qui effectuera la signature éventuelle.  En règle générale, cette clé se présente sous la forme d'un fichier .snk, qui peut être créé à l'aide de [outil Strong Name Tool \(Sn.exe\)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) fourni par le [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].  
  
2.  Annotez le code source de l'assembly avec deux attributs personnalisés de <xref:System.Reflection> :  
  
    -   <xref:System.Reflection.AssemblyKeyFileAttribute>, qui passe le nom du fichier contenant la clé publique en tant que paramètre à son constructeur.  
  
    -   <xref:System.Reflection.AssemblyDelaySignAttribute>, qui indique l'utilisation de la temporisation de signature en passant **true** en paramètre à son constructeur.  Par exemple :  
  
         [!code-cpp[AssemblyDelaySignAttribute#4](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cpp/source2.cpp#4)]
         [!code-csharp[AssemblyDelaySignAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cs/source2.cs#4)]
         [!code-vb[AssemblyDelaySignAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyDelaySignAttribute/vb/source2.vb#4)]  
  
3.  Le compilateur insère la clé publique dans le manifeste d'assembly et réserve de l'espace dans le fichier PE pour la signature de nom fort complet.  La clé publique réelle doit être stockée lors de la génération de l'assembly de sorte que d'autres assemblys référençant cet assembly puissent obtenir la clé à stocker dans leur propre référence d'assembly.  
  
4.  Étant donné que l'assembly n'a pas de signature de nom fort valide, la vérification de cette signature doit être désactivée.  Vous pouvez effectuer cette opération en utilisant l'option **–Vr** avec l'outil Strong Name Tool.  
  
     L'exemple suivant désactive la vérification pour un assembly appelé `myAssembly.dll`.  
  
    ```  
    sn –Vr myAssembly.dll  
    ```  
  
     Pour désactiver la vérification sur les plateformes où vous ne pouvez pas exécuter l'outil Strong NAME Tool, tels que les microprocesseurs de \(ARM\) de l'ordinateur Advanced RISC, utilisez l'option **–Vk** pour créer un fichier de registre.  Importer le fichier de registre dans le Registre de l'ordinateur sur lequel vous souhaitez désactiver la vérification.  L'exemple suivant crée un fichier de registre `myAssembly.dll`.  
  
    ```  
    sn –Vk myRegFile.reg myAssembly.dll  
    ```  
  
     Avec **–Vr** ou l'option **–Vk**, vous pouvez éventuellement inclure un fichier .snk pour la signature de test.  
  
    > [!CAUTION]
    >  Utilisez l'option **\-Vr** ou **–Vk** uniquement pendant le développement.  L'ajout d'un assembly à la liste des omissions de vérification crée une faille de sécurité.  Un assembly malveillant peut utiliser le nom complètement spécifié \(nom, version, culture et jeton de clé publique\) de l'assembly ajouté à la liste des omissions de vérification pour usurper son identité.  Cela permet également à l'assembly malveillant d'ignorer la vérification.  
  
    > [!NOTE]
    >  Si vous utilisez la temporisation de signature lorsque vous développez avec Visual Studio sur un ordinateur 64 bits, et que vous compilez un assembly pour n'importe quelle UC \( **Any CPU**\), vous devrez peut\-être appliquer l'option **\-Vr** deux fois. \(Dans Visual Studio, **Any CPU** est une valeur de la propriété de build **Plateforme cible**; lorsque vous compilez à partir de la ligne de commande, c'est la valeur par défaut.\) Pour exécuter votre application à partir de la ligne de commande ou de l'Explorateur de Fichiers Windows, utilisez la version 64 bits de [Sn.exe \(Strong Name Tool\)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) pour appliquer l'option **\-Vr** à l'assembly.  Pour charger l'assembly dans Visual Studio au moment du design \(par exemple, si l'assembly contient des composants utilisés par d'autres assemblys dans votre application\), utilisez la version 32 bits de l'outil Strong Name Tool.  Ceci s'explique par le fait que le compilateur juste\-à\-temps \(JIT\) compile l'assembly en code natif 64 bits lorsque l'assembly est exécuté à partir de la ligne de commande, et en code natif 32 bits lorsque l'assembly est chargé dans l'environnement au moment du design.  
  
5.  Vous soumettez l'assembly ultérieurement, généralement juste avant sa livraison, à l'Autorité de signature de la société pour la signature réelle de nom fort en utilisant l'option **–R** avec l'outil Strong Name Tool.  
  
     L'exemple suivant signe un assembly appelé `myAssembly.dll` avec un nom fort à l'aide de la paire de clés `sgKey.snk`.  
  
    ```  
    sn -R myAssembly.dll sgKey.snk  
    ```  
  
## Voir aussi  
 [Création d'assemblys](../../../docs/framework/app-domains/create-assemblies.md)   
 [Comment : créer une paire de clés publique\/privée](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md)   
 [Sn.exe \(Strong Name Tool\)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)   
 [Programmation à l'aide d'assemblys](../../../docs/framework/app-domains/programming-with-assemblies.md)