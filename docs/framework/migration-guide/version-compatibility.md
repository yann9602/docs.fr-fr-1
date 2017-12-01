---
title: "Compatibilité de versions dans le .NET Framework"
ms.custom: updateeachrelease
ms.date: 10/17/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
helpviewer_keywords:
- .NET Framework, version compatibility
- .NET Framework 4.5, compatibility with earlier versions
- .NET Framework versions, compatibility
ms.assetid: 2f25e522-456a-48c3-8a53-e5f39275649f
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 166d61339d2b74f378b50ade4b78fd41e9692f76
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
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
  
 À cause de cette restriction, les garanties de compatibilité sont particulièrement importantes pour les composants. Depuis .NET Framework 4, vous pouvez spécifier le degré auquel un composant est supposé rester compatible entre plusieurs versions en appliquant l'attribut <xref:System.Runtime.Versioning.ComponentGuaranteesAttribute?displayProperty=nameWithType> à ce composant. Les outils peuvent utiliser cet attribut pour détecter des violations potentielles de la garantie de compatibilité dans les versions ultérieures d'un composant.  
  
## <a name="backward-compatibility-and-the-net-framework-45"></a>Compatibilité descendante et .NET Framework 4.5  
 Le .NET Framework 4.5 et versions ultérieures sont à compatibilité descendante avec les applications qui ont été générées avec des versions antérieures du .NET Framework. En d’autres termes, applications et composants générés avec les versions précédentes fonctionnent sans modification sur le .NET Framework 4.5 et versions ultérieures. Toutefois, par défaut, les applications s’exécutent sur la version du common language runtime pour lequel elles ont été développées, il vous faudra peut-être fournir un fichier de configuration pour activer votre application s’exécute sur le .NET Framework 4.5 ou versions ultérieures. Pour plus d’informations, consultez la section [Compatibilité des versions pour les applications](#Apps) plus haut dans cet article.  
  
 Dans la pratique, cette compatibilité peut être arrêtée par des modifications apparemment sans importance du .NET Framework et des modifications des techniques de programmation. Par exemple, les améliorations des performances dans le .NET Framework 4.5 peuvent exposer une condition de concurrence critique qui ne se produit pas sur les versions antérieures. De la même façon, l’utilisation d’un chemin d’accès codé en dur aux assemblys .NET Framework, la comparaison d’égalité avec une version particulière du .NET Framework, et l’obtention de la valeur d’un champ privé à l’aide de la réflexion ne sont pas des pratiques à compatibilités descendante. De plus, chaque version du .NET Framework inclut des résolutions de bogue et des modifications relatives à la sécurité qui peuvent affecter la compatibilité de certains composants et applications.  
  
 Si votre application ou le composant ne fonctionne pas comme prévu sur le .NET Framework 4.5 (y compris ses versions intermédiaires, le [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7 ou 4.7.1, utilisez les listes de vérification suivantes :  
  
-  Si votre application a été développée pour s’exécuter sur n’importe quelle version du .NET Framework en commençant par le .NET Framework 4.0, consultez [compatibilité des applications dans le .NET Framework](application-compatibility.md) pour générer des listes des modifications entre votre version de .NET Framework ciblée et la version sur laquelle votre application est en cours d’exécution.  

- Si vous avez une application .NET Framework 3.5, consultez également [problèmes de Migration de .NET Framework 4](../../../docs/framework/migration-guide/net-framework-4-migration-issues.md).

- Si vous avez une application .NET Framework 2.0, consultez également [modifications dans .NET Framework 3.5 SP1](http://go.microsoft.com/fwlink/?LinkId=186989).

- Si vous avez une application .NET Framework 1.1, consultez également [modifications dans .NET Framework 2.0](http://go.microsoft.com/fwlink/?LinkID=125263).  
  
-   Si vous recompilez le code source existant pour s’exécuter sur le .NET Framework 4.5 ou de son point de mises en production, ou si vous développez une nouvelle version d’une application ou un composant qui cible le [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] ou ses versions intermédiaires à partir d’une vérification de base, de code source existante [ Nouveautés obsolètes dans la bibliothèque de classes](../../../docs/framework/whats-new/whats-obsolete.md) pour les types et membres obsolètes et appliquer la solution de contournement décrite. (Le code précédemment compilé continuera à s'exécuter sur des types et des membres marqués comme obsolètes.)  
  
-   Si vous déterminez qu’une modification du [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] a endommagé votre application, consultez le [schéma des paramètres d’exécution](../../../docs/framework/configure-apps/file-schema/runtime/index.md) pour déterminer si vous pouvez utiliser un paramètre d’exécution dans le fichier de configuration de votre application afin de restaurer le comportement précédent.  
  
-   Si vous rencontrez un problème qui n’est pas documenté, classez un bogue [Microsoft Connect](http://go.microsoft.com/fwlink/?LinkID=154815) et envoyez le numéro de bogue à [netfxcf@microsoft.com](mailto:netfxcf@microsoft.com).  
  
## <a name="compatibility-and-side-by-side-execution"></a>Compatibilité et exécution côte à côte  
 Si vous ne trouvez pas de solution de contournement appropriée pour votre problème, souvenez-vous que le .NET Framework 4.5, et ses versions intermédiaires, s’exécutent côte à côte avec les versions 1.1, 2.0 et 3.5, et qu’ils constituent une mise à jour intégrée qui remplace la version 4. Pour les applications ciblant les versions 1.1, 2.0 et 3.5, vous pouvez installer la version appropriée du .NET Framework sur l'ordinateur cible pour exécuter l'application dans l'environnement idéal. Pour plus d’informations sur l’exécution côte à côte, consultez [Exécution côte à côte](../../../docs/framework/deployment/side-by-side-execution.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Nouveautés](../../../docs/framework/whats-new/index.md)  
 [Éléments obsolètes dans la bibliothèque de classes](../../../docs/framework/whats-new/whats-obsolete.md)  
 [Compatibilité des applications](../../../docs/framework/migration-guide/application-compatibility.md)  
 [Politique de support pour Microsoft .NET Framework](http://go.microsoft.com/fwlink/p/?LinkId=248212)  
 [Problèmes de migration de .NET Framework 4](../../../docs/framework/migration-guide/net-framework-4-migration-issues.md)
