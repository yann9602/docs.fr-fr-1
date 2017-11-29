---
title: "Instructions de codage sécurisé"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managed wrapper to native code implementation
- secure coding
- reusable components
- library code that exposes protected resources
- code, security
- code security
- secure coding, options
- components [.NET Framework], security
- code security, options
- security-neutral code
- security [.NET Framework], coding guidelines
ms.assetid: 4f882d94-262b-4494-b0a6-ba9ba1f5f177
caps.latest.revision: "20"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3be1a51db31f18255eabe633cdeaeb860f9c8ce7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="secure-coding-guidelines"></a>Instructions de codage sécurisé
La sécurité basée sur les preuves et la sécurité d’accès du code fournissent des mécanismes particulièrement puissants et explicites d’implémentation de la sécurité. La plupart des codes d’application peuvent simplement utiliser l’infrastructure implémentée par le .NET Framework. Dans certains cas, une sécurité supplémentaire spécifique à l’application est nécessaire, générée via l’extension du système de sécurité ou via de nouvelles méthodes ad hoc.  
  
 Vous devez utiliser les autorisations appliquées par le .NET Framework et d’autres vérifications dans le code pour dresser des barrières visant à empêcher un code malveillant d’obtenir des informations que vous ne voulez pas partager ou d’effectuer d’autres actions indésirables. En outre, il vous faut trouver un compromis entre la sécurité et les possibilités d’utilisation dans tous les scénarios prévus qui utilisent du code de confiance.  
  
 Cette présentation décrit les différents procédés permettant de concevoir du code qui fonctionne avec le système de sécurité.  
  
## <a name="securing-resource-access"></a>Sécurisation de l’accès aux ressources  
 Lorsque vous concevez et écrivez votre code, vous devez protéger et limiter l’accès du code aux ressources, tout particulièrement quand vous utilisez ou appelez un code d’une origine inconnue. Par conséquent, ayez à l’esprit les techniques suivantes afin de garantir la sécurité de votre code :  
  
-   N’utilisez pas la sécurité d’accès du code (CAS, Code Access Security).  
  
-   N’utilisez pas du code de confiance partielle.  
  
-   N’utilisez pas .NET Remoting.  
  
-   N’utilisez pas le modèle COM distribué (Distributed Component Object Model, DCOM).  
  
-   N’utilisez pas de formateurs binaires.  
  
 La sécurité d’accès au code et le code transparent de sécurité ne seront pas pris en charge en tant que frontière de sécurité avec du code d’un niveau de confiance partiel. Nous vous déconseillons de charger et d'exécuter du code d'origine inconnue sans mettre en place d'autres mesures de sécurité. Les autres mesures de sécurité sont les suivantes :  
  
-   Virtualisation  
  
-   Conteneurs d’applications  
  
-   Utilisateurs et autorisations du système d’exploitation  
  
-   Conteneurs Hyper-V  
  
## <a name="security-neutral-code"></a>Code indépendant de la sécurité  
 Un code indépendant de la sécurité ne fait rien d’explicite avec le système de sécurité. Il s’exécute quelles que soient les autorisations qu’il reçoit. Des applications qui ne parviennent pas à intercepter les exceptions de sécurité associées à des opérations protégées (comme l’utilisation de fichiers, la mise en réseau, etc.) peuvent engendrer une exception non gérée, mais le code indépendant de la sécurité tire néanmoins parti des technologies de sécurité du .NET Framework.  
  
 Une bibliothèque indépendante de la sécurité possède des caractéristiques particulières que vous devez connaître. Supposons que votre bibliothèque fournisse des éléments d’API qui utilisent des fichiers ou appellent du code non managé. Si votre code ne possède pas l’autorisation correspondante, il ne s’exécutera pas comme décrit. Toutefois, même si le code possède cette autorisation, n’importe quel autre code d’application qui l’appelle doit avoir la même autorisation pour pouvoir fonctionner. Si le code appelant n’a pas l’autorisation appropriée, une <xref:System.Security.SecurityException> s’affiche à la suite le parcours de pile de code access security.  
  
## <a name="application-code-that-is-not-a-reusable-component"></a>Code d’application ne correspondant pas à un composant réutilisable  
 Si votre code fait partie d’une application qui ne sera pas appelée par un autre code, la sécurité est simple et un codage spécial peut ne pas être requis. Toutefois, n’oubliez pas qu’un code malveillant peut appeler votre code. Si la sécurité d’accès du code peut empêcher le code malveillant d’accéder à des ressources, ce type de code est toutefois capable de lire les valeurs de vos champs ou propriétés susceptibles de contenir des informations confidentielles.  
  
 De plus, si votre code accepte des entrées utilisateur à partir d’Internet ou d’autres sources peu fiables, vous devez vous méfier des entrées malveillantes.  
  
## <a name="managed-wrapper-to-native-code-implementation"></a>Implémentation d’un wrapper managé vers du code natif  
 Dans ce scénario, certaines fonctionnalités utiles sont implémentées dans du code natif que vous souhaitez mettre à la disposition du code managé. Il est aisé d’écrire des wrappers managés en utilisant l’appel de code non managé ou COM Interop. Toutefois, si vous procédez ainsi, les appelants de vos wrappers doivent avoir des droits de code non managé pour réussir. Dans le cadre de la stratégie par défaut, cela signifie que le code téléchargé depuis un intranet ou Internet ne fonctionne pas avec les wrappers.  
  
 Au lieu d’accorder des droits de code non managé à toutes les applications qui utilisent ces wrappers, il est préférable d’accorder ces droits uniquement au code wrapper. Si les fonctionnalités sous-jacentes n’exposent aucune ressource et que l’implémentation est également sécurisée, le wrapper doit simplement déclarer ses droits, ce qui permet à n’importe quel code d’effectuer un appel via celui-ci. Lorsque des ressources sont impliquées, le codage de sécurité doit être identique à l’exemple de code de bibliothèque décrit dans la section suivante. Comme le wrapper expose potentiellement les appelants à ces ressources, une vérification minutieuse de la sécurité du code natif est nécessaire. Celle-ci relève de la responsabilité du wrapper.  
  
## <a name="library-code-that-exposes-protected-resources"></a>Code de bibliothèque exposant des ressources protégées  
 Il s’agit de l’approche la plus puissante et donc la plus risquée (si elle n’est pas exécutée correctement) du codage de sécurité : votre bibliothèque sert d’interface permettant à un autre code d’accéder à certaines ressources qui ne sont pas disponibles autrement, tout comme les classes du .NET Framework appliquent des autorisations pour les ressources qu’elles utilisent. Chaque fois que vous exposez une ressource, votre code doit en premier lieu demander l’autorisation appropriée à la ressource (autrement dit, il doit effectuer une vérification de sécurité), puis généralement déclarer ses droits pour effectuer l’opération proprement dite.  
  
## <a name="related-topics"></a>Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Sécurisation des données d’état](../../../docs/standard/security/securing-state-data.md)|Décrit comment protéger les membres privés.|  
|[Sécurité et entrées d’utilisateur](../../../docs/standard/security/security-and-user-input.md)|Décrit les problèmes de sécurité liés à des applications qui acceptent les entrées utilisateur.|  
|[Sécurité et conditions de concurrence](../../../docs/standard/security/security-and-race-conditions.md)|Décrit comment éviter des conditions de concurrence critique dans votre code.|  
|[Sécurité et génération de code immédiate](../../../docs/standard/security/security-and-on-the-fly-code-generation.md)|Décrit les problèmes de sécurité liés à des applications qui génèrent du code dynamique.|  
|[Sécurité basée sur les rôles](../../../docs/standard/security/role-based-security.md)|Fournit une description détaillée de la sécurité basée sur les rôles de .NET Framework et explique comment l’utiliser dans votre code.|
