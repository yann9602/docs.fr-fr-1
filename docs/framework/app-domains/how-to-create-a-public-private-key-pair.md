---
title: "Comment&#160;: cr&#233;er une paire de cl&#233;s publique/priv&#233;e | Microsoft Docs"
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
  - "paires de clés pour assemblys avec nom fort"
  - "signer des assemblys"
  - "assemblys (.NET Framework), signer"
  - "paires de clés de chiffrement"
  - "fichiers snk (fichiers de paire)"
  - "paire de clés publique-privée"
  - "fichiers .snk"
  - "assemblys avec nom fort, paires de clés"
ms.assetid: 05026813-f3bd-4d7c-9e0b-fc588eb3d114
caps.latest.revision: 16
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 14
---
# Comment&#160;: cr&#233;er une paire de cl&#233;s publique/priv&#233;e
Pour signer un assembly avec un nom fort, vous devez avoir une paire de clés publique\/privée.  Cette paire de clés de chiffrement publique et privée est utilisée lors de la compilation pour créer un assembly avec nom fort.  Vous pouvez créer une paire de clés à l'aide de [outil Strong Name Tool \(Sn.exe\)](../../../docs/framework/tools/sn-exe-strong-name-tool.md).  Les fichiers de paire de clés ont généralement une extension .snk.  
  
> [!NOTE]
>  Dans [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], les pages de propriétés des projets C\# et Visual Basic comprennent un onglet **Signature** qui vous permet de sélectionner les fichiers de clés existants ou d'en générer de nouveaux sans utiliser Sn.exe.  Dans Visual C\+\+, vous pouvez spécifier l'emplacement d'un fichier de clé existant dans la page de propriétés **Avancé** de la section **Éditeur de liens** dans la section **Propriétés de configuration** de la **Pages de propriétés**.  L'utilisation de l'attribut <xref:System.Reflection.AssemblyKeyFileAttribute> pour identifier les paires de fichiers de clé est devenue obsolète dans [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)].  
  
### Pour créer une paire de clés  
  
1.  À l'invite de commandes, tapez la commande suivante :  
  
     **sn –k** \<*nom du fichier*\>  
  
     Dans cette commande, *nom du fichier* représente le nom du fichier de sortie contenant la paire de clés.  
  
 L'exemple suivant crée une paire de clés appelée `sgKey.snk`.  
  
```  
sn -k sgKey.snk  
```  
  
 Si vous avez l'intention de temporiser la signature d'un assembly et si vous contrôlez entièrement la paire de clés \(ce qui est improbable en dehors des scénarios de test\), vous pouvez utiliser les commandes suivantes pour générer une paire de clés, puis en extraire la clé publique dans un fichier distinct.  Créez tout d'abord la paire de clés :  
  
```  
sn -k keypair.snk  
```  
  
-   Ensuite, extrayez la clé publique de la paire de clés et copiez\-la dans un fichier distinct :  
  
```  
sn -p keypair.snk public.snk  
```  
  
-   Une fois la paire de clés créée, vous devez placer le fichier à un emplacement où les outils de signature de nom fort puissent le trouver.  
  
 Lorsque vous signez un assembly avec un nom fort, l'utilitaire [Assembly Linker \(Al.exe\)](../../../docs/framework/tools/al-exe-assembly-linker.md) recherche le fichier de clé relatif au répertoire en cours et au répertoire de sortie.  Lorsque vous utilisez des compilateurs de ligne de commande, vous pouvez vous contenter de copier la clé dans le répertoire en cours contenant vos modules de code.  
  
 Si vous utilisez une version antérieure de [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] ne disposant pas de l'onglet **Signature** dans les propriétés de projet, l'emplacement de fichier de clé recommandé est le répertoire de projet avec l'attribut de fichier spécifié comme suit :  
  
 [!code-cpp[AssemblyName_KeyPair#21](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyName_KeyPair/CPP/keyfileattrib.cpp#21)]
 [!code-csharp[AssemblyName_KeyPair#21](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyName_KeyPair/CS/keyfileattrib.cs#21)]
 [!code-vb[AssemblyName_KeyPair#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyName_KeyPair/VB/keyfileattrib.vb#21)]  
  
## Voir aussi  
 [Création et utilisation d'assemblys avec nom fort](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)