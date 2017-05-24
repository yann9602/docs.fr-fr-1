---
title: "Compatibilité de versions dans le .NET Framework | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .NET Framework, version compatibility
- .NET Framework 4.5, compatibility with earlier versions
- .NET Framework versions, compatibility
ms.assetid: 2f25e522-456a-48c3-8a53-e5f39275649f
caps.latest.revision: 35
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 09f682d9c3a1cf5d42bba878676d84b9328a1a81
ms.contentlocale: fr-fr
ms.lasthandoff: 05/22/2017

---
# <a name="version-compatibility-in-the-net-framework"></a>Compatibilité de versions dans le .NET Framework
La compatibilité descendante signifie qu'une application développée pour une version particulière d'une plateforme s'exécutera sur les versions ultérieures de cette plateforme. Le .NET Framework essaie d'optimiser la compatibilité descendante : le code source écrit pour une version du .NET Framework doit se compiler sur les versions ultérieures du .NET Framework, et les fichiers binaires qui s'exécutent sur une version du .NET Framework doivent se comporter de la même manière sur les versions ultérieures du .NET Framework.  
  
<a name="Apps"></a>   
## <a name="version-compatibility-for-apps"></a>Compatibilité des versions pour les applications  
 Par défaut, une application s'exécute sur la version .NET Framework pour laquelle elle a été générée. Si cette version n'est pas présente et si le fichier de configuration de l'application ne définit pas les versions prises en charge, une erreur d'initialisation du .NET Framework peut se produire. Dans ce cas, la tentative d'exécution de l'application échouera.  
  
 Pour définir les versions spécifiques sur lesquelles votre application s’exécute, ajoutez un ou plusieurs éléments [\<supportedRuntime>](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) dans le fichier de configuration de votre application. Chaque élément `<supportedRuntime>` fournit une liste des versions prises en charge de l'exécution ; la première spécifie la version préférée et la dernière correspond à la version la moins préférée.  
  
```xml  
<configuration>  
   <startup>  
      <supportedRuntime version="v2.0.50727" />  
      <supportedRuntime version="v4.0" />  
   </startup>  
</configuration>  
```  
  
 Pour plus d’informations, consultez [Guide pratique pour configurer une application en vue de prendre en charge le .NET Framework 4 ou 4.x](../../../docs/framework/migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md).  
  
## <a name="version-compatibility-for-components"></a>Compatibilité des versions pour les composants  
 Une application peut contrôler la version .NET Framework sur laquelle elle s'exécute, mais un composant ne le peut pas. Les composants et bibliothèques de classes sont chargés dans le contexte d'une application particulière et s'exécutent donc automatiquement sur la version du .NET Framework sur lequel l'application s'exécute.  
  
 À cause de cette restriction, les garanties de compatibilité sont particulièrement importantes pour les composants. Depuis .NET Framework 4, vous pouvez spécifier le degré auquel un composant est supposé rester compatible entre plusieurs versions en appliquant l'attribut <xref:System.Runtime.Versioning.ComponentGuaranteesAttribute?displayProperty=fullName> à ce composant. Les outils peuvent utiliser cet attribut pour détecter des violations potentielles de la garantie de compatibilité dans les versions ultérieures d'un composant.  
  
## <a name="backward-compatibility-and-the-net-framework-45"></a>Compatibilité descendante et .NET Framework 4.5  
 Le .NET Framework 4.5 et ses versions intermédiaires (4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2 et 4.7) présentent une compatibilité descendante avec les applications générées à l’aide des versions antérieures du .NET Framework. En d'autres termes, les applications et composants générés avec les versions antérieures du .NET Framework fonctionneront sur .NET Framework 4.5 sans être modifiés. Toutefois, par défaut, les applications sont exécutées sur la version du Common Language Runtime pour laquelle elles ont été développées. Par conséquent, il est possible que vous deviez fournir un fichier de configuration pour permettre à votre application de s'exécuter sur .NET Framework 4.5. Pour plus d’informations, consultez la section [Compatibilité des versions pour les applications](#Apps) plus haut dans cet article.  
  
 Dans la pratique, cette compatibilité peut être arrêtée par des modifications apparemment sans importance du .NET Framework et des modifications des techniques de programmation. Par exemple, les améliorations des performances dans le .NET Framework 4.5 peuvent exposer une condition de concurrence critique qui ne se produit pas sur les versions antérieures. De la même façon, l’utilisation d’un chemin d’accès codé en dur aux assemblys .NET Framework, la comparaison d’égalité avec une version particulière du .NET Framework, et l’obtention de la valeur d’un champ privé à l’aide de la réflexion ne sont pas des pratiques à compatibilités descendante. De plus, chaque version du .NET Framework inclut des résolutions de bogue et des modifications relatives à la sécurité qui peuvent affecter la compatibilité de certains composants et applications.  
  
 Si votre application ou composant ne fonctionne pas comme prévu sur le .NET Framework 4.5 (y compris ses versions intermédiaires, [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] 4.5.2, 4.6, 4.6.1, 4.6.2 ou 4.7), utilisez les listes de vérification suivantes :  
  
-   Consultez ces rubriques pour rechercher les modifications qui peuvent affecter votre application et appliquez la solution de contournement décrite :  
  
    -   [Problèmes de migration de .NET Framework 4](http://go.microsoft.com/fwlink/p/?LinkId=248212)  
  
    -   [Compatibilité des applications dans la version 4.5](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5.md)  
  
    -   [Compatibilité des applications dans la version 4.5.1](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5-1.md)  
  
    -   [Compatibilité des applications dans la version 4.5.2](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5-2.md)  
  
    -   [Compatibilité des applications dans la version 4.6](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6.md)  
  
    -   [Compatibilité des applications dans la version 4.6.1](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-1.md)  
  
    -   [Compatibilité des applications dans la version 4.6.2](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-2.md)  

    - [Compatibilité des applications dans la version 4.7](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-2.md)
       
-   Si vous possédez une application .NET Framework 1.1, passez également en revue les rubriques suivantes :  
  
    -   [Modifications dans .NET Framework 2.0](http://go.microsoft.com/fwlink/?LinkID=125263)  
  
    -   [Modifications dans .NET Framework 3.5 SP1](http://go.microsoft.com/fwlink/?LinkId=186989)  
  
-   Si vous recompilez le code source existant pour l’exécuter sur .NET Framework 4.5 ou ses versions intermédiaires, ou si vous développez une nouvelle version d’une application ou d’un composant qui cible le [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] à partir d’une base de code source existante, consultez [Éléments obsolètes dans la bibliothèque de classes](../../../docs/framework/whats-new/whats-obsolete.md) pour connaître les types et les membres obsolètes, et appliquer la solution de contournement décrite. (Le code précédemment compilé continuera à s'exécuter sur des types et des membres marqués comme obsolètes.)  
  
-   Si vous déterminez qu’une modification du [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] a endommagé votre application, consultez le [schéma des paramètres d’exécution](../../../docs/framework/configure-apps/file-schema/runtime/index.md) pour déterminer si vous pouvez utiliser un paramètre d’exécution dans le fichier de configuration de votre application afin de restaurer le comportement précédent.  
  
-   Si vous rencontrez un problème qui n’est pas documenté, classez un bogue [Microsoft Connect](http://go.microsoft.com/fwlink/?LinkID=154815) et envoyez le numéro de bogue à [netfxcf@microsoft.com](mailto:netfxcf@microsoft.com).  
  
## <a name="compatibility-and-side-by-side-execution"></a>Compatibilité et exécution côte à côte  
 Si vous ne trouvez pas de solution de contournement appropriée pour votre problème, souvenez-vous que le .NET Framework 4.5, et ses versions intermédiaires, s’exécutent côte à côte avec les versions 1.1, 2.0 et 3.5, et qu’ils constituent une mise à jour intégrée qui remplace la version 4. Pour les applications ciblant les versions 1.1, 2.0 et 3.5, vous pouvez installer la version appropriée du .NET Framework sur l'ordinateur cible pour exécuter l'application dans l'environnement idéal. Pour plus d’informations sur l’exécution côte à côte, consultez [Exécution côte à côte](../../../docs/framework/deployment/side-by-side-execution.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Nouveautés](../../../docs/framework/whats-new/index.md)   
 [Éléments obsolètes dans la bibliothèque de classes](../../../docs/framework/whats-new/whats-obsolete.md)   
 [Compatibilité des applications](../../../docs/framework/migration-guide/application-compatibility.md)   
 [Politique de support pour Microsoft .NET Framework](http://go.microsoft.com/fwlink/p/?LinkId=248212)   
 [Problèmes de migration de .NET Framework 4](http://go.microsoft.com/fwlink/p/?LinkId=248212)

