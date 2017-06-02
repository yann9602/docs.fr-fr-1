---
title: "Erreurs d&#39;initialisation de .NET&#160;Framework&#160;: g&#233;rer l&#39;exp&#233;rience utilisateur | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - ".NET Framework, erreurs d'initialisation"
  - "erreurs d'initialisation (.NET Framework)"
  - "aucune expérience d'infrastructure"
ms.assetid: 680a7382-957f-4f6e-b178-4e866004a07e
caps.latest.revision: 5
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 5
---
# Erreurs d&#39;initialisation de .NET&#160;Framework&#160;: g&#233;rer l&#39;exp&#233;rience utilisateur
Le système de lancement du Common Langage Runtime \(CLR\) détermine la version du CLR qui sera utilisé pour exécuter du code d'application managé.  Dans certains cas, le système de lancement peut ne pas être en mesure de trouver une version du CLR à charger.  Cette situation se produit généralement lorsqu'une application requiert une version du CLR qui est incorrecte ou non installée sur un ordinateur donné.  Si la version demandée est introuvable, le système de lancement du CLR retourne un code d'erreur HRESULT de la fonction ou de l'interface appelée, et peut afficher un message d'erreur à l'utilisateur qui exécute l'application.  Cet article fournit une liste de codes HRESULT et montre comment empêcher le message d'erreur de s'afficher.  
  
 Le CLR fournit l'infrastructure de rapports pour vous aider à déboguer des problèmes de lancement du CLR, comme décrit dans [Comment : déboguer les problèmes d'activation du CLR](../../../docs/framework/deployment/how-to-debug-clr-activation-issues.md).  Cette infrastructure ne doit pas être confondue avec les [journaux de liaison d'assembly](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md), qui sont totalement différents.  
  
## Codes HRESULT de lancement du CLR  
 L'API de lancement du CLR retourne des codes HRESULT pour informer un hôte du résultat d'une opération de lancement.  Les hôtes CLR doivent toujours consulter ces valeurs de retour avant de poursuivre d'autres opérations supplémentaires.  
  
-   CLR\_E\_SHIM\_RUNTIMELOAD  
  
-   CLR\_E\_SHIM\_RUNTIMEEXPORT  
  
-   CLR\_E\_SHIM\_INSTALLROOT  
  
-   CLR\_E\_SHIM\_INSTALLCOMP  
  
-   CLR\_E\_SHIM\_LEGACYRUNTIMEALREADYBOUND  
  
-   CLR\_E\_SHIM\_SHUTDOWNINPROGRESS  
  
## Interface utilisateur pour les erreurs d'initialisation  
 Si le système de lancement du CLR ne peut pas charger la version correcte du runtime qui est requis par une application, il affiche un message d'erreur aux utilisateurs pour leur informer que leur ordinateur n'est pas correctement configuré pour exécuter l'application, et leur fournit la possibilité de remédier à cette situation.  Le message d'erreur suivant est généralement présenté dans cette situation.  L'utilisateur peut choisir **Oui** pour accéder à un site Web Microsoft où ils peuvent télécharger la version du .NET Framework appropriée pour l'application.  
  
 ![Boîte de dialogue d'erreur d'initialisation .NET Framework](../../../docs/framework/deployment/media/initerrordialog.png "InitErrorDialog")  
Message d'erreur standard pour les erreurs d'initialisation  
  
## Résoudre l'erreur d'initialisation  
 En tant que développeur, vous avez diverses options pour contrôler le message d'erreur d'initialisation du .NET Framework.  Par exemple, vous pouvez utiliser une balise de l'API pour empêcher le message d'être affiché, comme décrit dans la section suivante.  Toutefois, vous devez toujours résoudre le problème qui a empêché l'application de charger le runtime demandé.  Sinon, votre application peut ne pas s'exécuter, ou certaines fonctionnalités peuvent ne pas être disponible.  
  
 Pour résoudre les problèmes sous\-jacents et fournir une meilleure expérience utilisateur \(moins de messages d'erreur\), nous recommandons ce qui suit :  
  
-   Pour les applications du .NET Framework 3.5 \(ou version antérieure\) : Configurez votre application pour prendre en charge le .NET Framework 4 ou 4,5 \(voir les [instructions ici](../../../docs/framework/migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)\).  
  
-   Pour les applications du .NET Framework 4 : Installez le package redistribuable du .NET Framework 4 dans le cadre de l'installation de votre application.  Consultez [Guide de déploiement pour les développeurs](../../../docs/framework/deployment/deployment-guide-for-developers.md).  
  
## Contrôle du message d'erreur  
 Afficher un message d'erreur pour communiquer qu'une version du .NET Framework demandée est introuvable peut être vu soit comme un service utile ou comme un petit désagrément utilisateur.  Dans les deux cas, vous pouvez contrôler l'interface utilisateur en passant des balises aux APIs de lancement.  
  
 La méthode [ICLRMetaHostPolicy::GetRequestedRuntime](../Topic/ICLRMetaHostPolicy::GetRequestedRuntime%20Method.md) reçoit un membre de l'énumération [METAHOST\_POLICY\_FLAGS](../../../ocs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md) comme entrée.  Incluez la balise METAHOST\_POLICY\_SHOW\_ERROR\_DIALOG pour demander un message d'erreur si la version du CLR demandée est introuvable.  Par défaut, le message d'erreur n'est pas affiché. \(La méthode [ICLRMetaHost::GetRuntime](../Topic/ICLRMetaHost::GetRuntime%20Method.md) n'accepte pas cette balise, et ne fournit aucune autre façon d'afficher le message d'erreur.\)  
  
 Windows fournit une fonction [SetErrorMode](http://go.microsoft.com/fwlink/p/?LinkID=255242) que vous pouvez utiliser pour déclarer si vous souhaitez ou non afficher les messages d'erreur provoqués par le code qui s'exécute dans votre processus.  Spécifiez la balise SEM\_FAILCRITICALERRORS pour empêcher que le message d'erreur s'affiche.  
  
 Toutefois, dans certains cas, il est important de substituer un processus d'application au paramètre SEM\_FAILCRITICALERRORS.  Par exemple, si vous avez un composant COM natif qui héberge le CLR et qui est hébergé dans un processus où SEM\_FAILCRITICALERRORS est défini, vous pouvez vouloir substituer la balise, selon l'impact qu'a l'affichage des messages d'erreur dans ce processus d'application spécifique.  Dans ce cas, vous pouvez utiliser l'une des balises suivantes pour remplacer SEM\_FAILCRITICALERRORS :  
  
-   Utiliser METAHOST\_POLICY\_IGNORE\_ERROR\_MODE avec la méthode [ICLRMetaHostPolicy::GetRequestedRuntime](../Topic/ICLRMetaHostPolicy::GetRequestedRuntime%20Method.md).  
  
-   Utiliser RUNTIME\_INFO\_IGNORE\_ERROR\_MODE avec la fonction [GetRequestedRuntimeInfo](../../../ocs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md).  
  
## La stratégie IU des hôtes fournis par le CLR  
 Le CLR inclut un ensemble d'hôtes pour divers scénarios, et tous les hôtes affichent un message d'erreur lorsqu'ils rencontrent des problèmes pour charger la version requise du runtime.  Le tableau suivant fournit une liste d'hôtes et leurs politiques de message d'erreur.  
  
|Hôte CLR|Description|Stratégie de messages d'erreur|Le message d'erreur peut\-il être désactivé ?|  
|--------------|-----------------|------------------------------------|---------------------------------------------------|  
|Hôte EXE managé|Lance des EXEs managés.|Est affiché en cas de version du .NET Framework manquante.|Non|  
|Hôte COM managé|Charge des composants COM managés dans un processus.|Est affiché en cas de version du .NET Framework manquante.|Oui, en définissant la balise SEM\_FAILCRITICALERRORS|  
|Hôte ClickOnce|Démarre les applications ClickOnce.|Est affiché en cas de version du .NET Framework manquant, à partir de la version [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]|Non|  
|Hôte XBAP|Démarre les applications WPF XBAP.|Est affiché en cas de version du .NET Framework manquant, à partir de la version [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]|Non|  
  
## Comportement et interface utilisateur de [!INCLUDE[win8](../../../includes/win8-md.md)].  
 Le système de lancement du CLR fournit les mêmes comportements et interfaces utilisateurs sur [!INCLUDE[win8](../../../includes/win8-md.md)] que sur d'autres versions du système d'exploitation Windows, sauf lorsqu'il rencontre des problèmes pour charger le CLR 2.0.  [!INCLUDE[win8](../../../includes/win8-md.md)] inclut [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], qui utilise le CLR 4.5. Toutefois, [!INCLUDE[win8](../../../includes/win8-md.md)] n'inclut pas les .NET Framework 2.0, 3.0 ou 3.5, qui utilisent tous CLR 2.0.  Par conséquent, les applications qui dépendent du CLR 2.0 ne fonctionnent pas dans [!INCLUDE[win8](../../../includes/win8-md.md)] par défaut.  À la place, ils affichent la boîte de dialogue suivante pour permettre aux utilisateurs d'installer le .NET Framework 3.5.  Les utilisateurs peuvent également activer le .NET Framework 3.5 dans le panneau de configuration.  Les deux options sont décrites dans l'article [Installing the .NET Framework 3.5 on Windows 8 and later versions](../../../docs/framework/install/net-framework-3-5-on-windows-8-plus.md).  
  
 ![Boîte de dialogue pour l'installation 3.5 sur Windows 8](../../../docs/framework/deployment/media/installdialog.png "installdialog")  
Invite à installer .NET Framework 3.5 à la demande  
  
> [!NOTE]
>  [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] remplace le .NET Framework 4 \(CLR 4\) sur l'ordinateur de l'utilisateur.  Par conséquent, les applications du .NET Framework 4 fonctionnent de façon transparente, sans afficher cette boîte de dialogue, dans [!INCLUDE[win8](../../../includes/win8-md.md)].  
  
 Lorsque le .NET Framework 3.5 est installé, les utilisateurs peuvent exécuter leurs applications qui dépendent du .NET Framework 2.0, 3.0, ou 3.5 sur leurs ordinateurs [!INCLUDE[win8](../../../includes/win8-md.md)].  Ils peuvent également exécuter des applications du .NET Framework 1.0 et 1.1, à condition que ces applications ne soient pas explicitement configurées pour s'exécuter uniquement sur le .NET Framework 1.0 ou 1.1.  Consultez [Migration à partir du .NET Framework 1.1](../../../docs/framework/migration-guide/migrating-from-the-net-framework-1-1.md).  
  
 En commençant par [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], la journalisation du lancement du CLR a été améliorée pour inclure les entrées de journal enregistrant quand et pourquoi le message d'erreur d'initialisation est affiché.  Pour plus d'informations, consultez [Comment : déboguer les problèmes d'activation du CLR](../../../docs/framework/deployment/how-to-debug-clr-activation-issues.md).  
  
## Voir aussi  
 [Guide de déploiement pour les développeurs](../../../docs/framework/deployment/deployment-guide-for-developers.md)   
 [Comment : configurer une application pour prendre en charge le .NET Framework 4 ou 4.5](../../../docs/framework/migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)   
 [Comment : déboguer les problèmes d'activation du CLR](../../../docs/framework/deployment/how-to-debug-clr-activation-issues.md)   
 [Installing the .NET Framework 3.5 on Windows 8 and later versions](../../../docs/framework/install/net-framework-3-5-on-windows-8-plus.md)