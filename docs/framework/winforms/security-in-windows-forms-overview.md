---
title: "Vue d'ensemble de la sécurité dans les Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code access security [Windows Forms], Windows Forms
- permissions [Windows Forms], Windows Forms
- Windows Forms, security
- security [Windows Forms], about security
- access control [Windows Forms], Windows Forms
ms.assetid: 4810dc9f-ea23-4ce1-8ea1-657f0ff1d820
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 63b7b704cf5d69ea2186ddef6e86f5c6d7993778
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="security-in-windows-forms-overview"></a>Vue d'ensemble de la sécurité dans les Windows Forms
Avant la publication de [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], tout code exécuté sur l'ordinateur d'un utilisateur avait les mêmes droits ou autorisations d'accéder aux ressources que l'utilisateur de l'ordinateur. Par exemple, si l'utilisateur était autorisé à accéder au système de fichiers, le code était autorisé à accéder au système de fichiers. Si l'utilisateur était autorisé à accéder à une base de données, le code était autorisé à accéder à cette base de données. Bien que ces droits ou autorisations puissent être acceptables pour le code dans les exécutables que l'utilisateur a explicitement installé sur l'ordinateur local, ils peuvent ne pas être acceptables pour le code potentiellement malveillant provenant d'Internet ou d'un intranet local. Ce code ne doit pas pouvoir accéder aux ressources de l'ordinateur de l'utilisateur sans autorisation.  
  
 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] introduit une infrastructure appelée Sécurité d'accès du code qui vous permet de différencier les autorisations, ou droits, dont disposent le code des droits dont disposent l'utilisateur. Par défaut, le code provenant d'Internet et de l'intranet peut uniquement s'exécuter dans un mode qui porte le nom de confiance partielle. La confiance partielle soumet une application à une série de restrictions : entre autres, une application ne peut pas accéder au disque dur local et ne peut pas exécuter de code non managé. [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] contrôle les ressources auxquelles le code est autorisé à accéder en fonction de l’identité de ce code : d’où il provient, s’il comporte des [assemblys avec nom fort](../../../docs/framework/app-domains/strong-named-assemblies.md), s’il est signé avec un certificat, etc.  
  
 La technologie [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)], qui vous permet de déployer des applications Windows Forms, simplifie le développement des applications qui s'exécutent avec une confiance partielle, avec une confiance totale ou avec une confiance partielle avec des autorisations élevées. [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] fournit des fonctionnalités telles que l'élévation d'autorisations et le déploiement d'applications approuvées pour que votre application puisse demander une confiance totale ou des autorisations élevées à l'utilisateur local de manière responsable.  
  
## <a name="understanding-security-in-the-net-framework"></a>Présentation de la sécurité dans .NET Framework  
 La sécurité d'accès du code permet au code d'avoir un niveau de confiance à différents degrés, en fonction de son origine et d'autres aspects de son identité. Pour plus d’informations sur les preuves utilisées par le Common Language Runtime afin de déterminer la stratégie de sécurité, consultez [Preuve](http://msdn.microsoft.com/en-us/64ceb7c8-a0b4-46c4-97dc-6c22da0539da). Elle vous aide à protéger les systèmes contre les programmes malveillants et à empêcher que le code approuvé ne compromette la sécurité de manière intentionnelle ou accidentelle. La sécurité d'accès du code vous permet aussi de mieux contrôler les actions que votre application peut effectuer, car vous pouvez spécifier uniquement les autorisations dont elle a besoin. La sécurité d'accès du code affecte tout le code managé qui cible le Common Language Runtime, même si ce code ne fait aucune vérification d'autorisation de sécurité d'accès du code. Pour plus d’informations sur la sécurité dans [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], consultez [Concepts fondamentaux sur la sécurité](../../../docs/standard/security/key-security-concepts.md) et [Notions fondamentales de la sécurité d’accès du code](../../../docs/framework/misc/code-access-security-basics.md).  
  
 Si l’utilisateur exécute un fichier exécutable Windows Forms directement à partir d’un serveur web ou d’un partage de fichiers, le degré de confiance accordé à votre application dépend de l’emplacement du code et de la façon dont il est démarré. Quand une application s'exécute, elle est évaluée automatiquement et le Common Language Runtime lui affecte un jeu d'autorisations nommé. Par défaut, le code sur l'ordinateur local dispose du jeu d'autorisations Confiance totale, le code provenant d'un réseau local dispose du jeu d'autorisations Intranet local et le code provenant d'Internet dispose du jeu d'autorisations Internet.  
  
> [!NOTE]
>  Dans [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] version 1.0 Service Pack 1 et Service Pack 2, le groupe de code de la zone Internet reçoit le jeu d'autorisations Rien. Dans toutes les autres versions de [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], le groupe de code de la zone Internet reçoit le jeu d'autorisations Internet.  
>   
>  Les autorisations par défaut accordées dans chacun de ces jeux d’autorisations sont répertoriées dans la rubrique [Stratégie de sécurité par défaut](http://msdn.microsoft.com/en-us/2c086873-0894-4f4d-8f7e-47427c1a3b55). En fonction des autorisations reçues par l'application, elle s'exécute correctement ou génère une exception de sécurité.  
>   
>  De nombreuses applications Windows Forms seront déployées à l'aide de [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)]. Les outils utilisés pour générer un déploiement [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] ont des paramètres de sécurité par défaut différents de ceux mentionnés plus haut. Pour plus d'informations, voir la discussion suivante.  
  
 Les autorisations réellement accordées à votre application peuvent être différentes des valeurs par défaut, car la stratégie de sécurité peut être modifiée. Cela signifie que votre application peut avoir une autorisation sur un ordinateur, mais pas sur un autre.  
  
## <a name="developing-a-more-secure-windows-forms-application"></a>Développement d'une application Windows Forms plus sécurisée  
 La sécurité est importante lors de toutes les étapes du développement d'application. Commencez par examiner et suivre les [Instructions de codage sécurisé](../../../docs/standard/security/secure-coding-guidelines.md).  
  
 Ensuite, décidez si votre application doit s'exécuter avec une confiance totale ou partielle. L'exécution de votre application avec une confiance totale facilite l'accès aux ressources sur l'ordinateur local, mais expose votre application et ses utilisateurs à des risques de sécurité élevés si vous ne concevez et ne développez pas votre application en respectant strictement les consignes fournies dans la rubrique Instructions de codage sécurisé. L'exécution de votre application avec une confiance partielle simplifie le développement d'une application plus sécurisée et réduit considérablement les risques, mais nécessite davantage de planification quant à l'implémentation de certaines fonctionnalités.  
  
 Si vous choisissez la confiance partielle (autrement dit, le jeux d'autorisation Internet ou Intranet local), choisissez comment votre application doit se comporter dans cet environnement. Windows Forms fournit des méthodes alternatives et plus sûres pour implémenter des fonctionnalités dans un environnement de confiance partielle. Certaines parties de votre application, comme l'accès aux données, peuvent être conçues et écrites différemment pour les environnements de confiance partielle et de confiance totale. Certaines fonctionnalités de Windows Forms, telles que les paramètres d’application, sont conçues pour fonctionner en mode de confiance partielle. Pour plus d’informations, consultez [Vue d’ensemble des paramètres d’application](../../../docs/framework/winforms/advanced/application-settings-overview.md).  
  
 Si votre application a besoin de davantage d'autorisations que celles offertes par la confiance partielle mais que vous ne souhaitez pas l'exécuter avec une confiance totale, vous pouvez l'exécuter avec une confiance partielle en déclarant uniquement les autorisations supplémentaires dont vous avez besoin. Par exemple, si vous souhaitez l'exécuter avec une confiance partielle mais que vous devez l'autoriser à accéder en lecture seule à un répertoire dans le système de fichiers de l'utilisateur, vous pouvez demander <xref:System.Security.Permissions.FileIOPermission> uniquement pour ce répertoire. Utilisée correctement, cette approche peut procurer à votre application des fonctionnalités supplémentaires et minimiser les risques de sécurité pour vos utilisateurs.  
  
 Quand vous développez une application qui s'exécute avec une confiance partielle, effectuez le suivi des autorisations dont votre application doit disposer et de celles qu'elle pourrait éventuellement utiliser. Quand toutes les autorisations sont connues, vous devez effectuer une demande déclarative pour disposer de l'autorisation au niveau de l'application. La demande d'autorisation indique au Runtime [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] les autorisations dont votre application a besoin et celles dont elle ne souhaite pas spécifiquement bénéficier. Pour plus d’informations sur les demandes d’autorisations, consultez [Demande d’autorisations](http://msdn.microsoft.com/en-us/0447c49d-8cba-45e4-862c-ff0b59bebdc2).  
  
 Quand vous demandez des autorisations facultatives, vous devez gérer les exceptions de sécurité qui seront générées si votre application effectue une action qui nécessite des autorisations qui ne lui ont pas été accordées. Une gestion appropriée de <xref:System.Security.SecurityException> garantit que votre application peut continuer à fonctionner. Votre application peut utiliser l’exception pour déterminer si une fonctionnalité doit être désactivée pour l’utilisateur. Par exemple, une application peut désactiver l’option de menu **Enregistrer** si l’autorisation de fichier nécessaire n’est pas accordée.  
  
 Il est parfois difficile de savoir si vous avez déclaré toutes les autorisations requises. Par exemple, un appel de méthode apparemment anodin peut accéder au système de fichiers à un moment donné de son exécution. Si vous ne déployez pas votre application avec toutes les autorisations requises, les tests peuvent réussir lors du débogage sur votre bureau, mais échouer lors du déploiement. Le Kit SDK [!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)] et [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] contiennent tous deux des outils permettant de calculer les autorisations dont une application a besoin : l'outil en ligne de commande MT.exe et la fonctionnalité Calculer les autorisations de [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], respectivement.  
  
 Les rubriques suivantes décrivent les fonctionnalités de sécurité supplémentaires de Windows Forms.  
  
|Rubrique|Description|  
|-----------|-----------------|  
|-   [Accès plus sécurisé aux fichiers et aux données dans les Windows Forms](../../../docs/framework/winforms/more-secure-file-and-data-access-in-windows-forms.md)|Décrit comment accéder aux fichiers et aux données dans un environnement de confiance partielle.|  
|-   [Impression plus sécurisée dans les Windows Forms](../../../docs/framework/winforms/more-secure-printing-in-windows-forms.md)|Décrit comment accéder aux fonctionnalités d’impression dans un environnement de confiance partielle.|  
|-   [Considérations supplémentaires sur la sécurité des Windows Forms](../../../docs/framework/winforms/additional-security-considerations-in-windows-forms.md)|Décrit comment manipuler des fenêtres, utiliser le Presse-papiers et effectuer des appels au code non managé dans un environnement de confiance partielle.|  
  
-  
  
### <a name="deploying-an-application-with-the-appropriate-permissions"></a>Déploiement d'une application avec les autorisations appropriées  
 L'approche la plus courante pour déployer une application Windows Forms sur un ordinateur client consiste à utiliser [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)], une technologie de déploiement qui décrit tous les composants dont votre application a besoin pour s'exécuter. [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] utilise des fichiers XML appelés manifestes pour décrire les assemblys et les fichiers qui composent votre application, ainsi que les autorisations requises.  
  
 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] dispose de deux technologies permettant de demander des autorisations élevées sur un ordinateur client. Ces deux technologies reposent sur l'utilisation de certificats Authenticode. Les certificats permettent de garantir à vos utilisateurs que l'application provient d'une source approuvée.  
  
 Le tableau suivant décrit ces technologies.  
  
|Technologie d'élévation d'autorisations|Description|  
|------------------------------------|-----------------|  
|Élévation d'autorisations|Affiche une boîte de dialogue de sécurité la première fois que votre application s'exécute. La boîte de dialogue **Élévation d’autorisations** indique à l’utilisateur le nom de la personne qui a publié l’application, pour qu’il puisse décider en connaissance de cause s’il doit lui accorder une confiance supplémentaire|  
|Déploiement d'applications approuvées|Exige qu'un administrateur système effectue une installation ponctuelle du certificat Authenticode de l'éditeur sur un ordinateur client. Après cela, toutes les applications signées avec le certificat sont considérées comme approuvées et peuvent s'exécuter avec une confiance totale sur l'ordinateur local sans invite supplémentaire.|  
  
 La technologie adoptée dépendra de votre environnement de déploiement. Pour plus d’informations, consultez [Choix d’une stratégie de déploiement ClickOnce](/visualstudio/deployment/choosing-a-clickonce-deployment-strategy).  
  
 Par défaut, les applications [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] déployées à l'aide des outils de [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] ou du Kit SDK [!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)] (Mage.exe et MageUI.exe) sont configurées pour s'exécuter sur un ordinateur client qui dispose de la confiance totale. Si vous déployez votre application avec une confiance partielle ou en utilisant uniquement certaines autorisations supplémentaires, vous devez modifier ce comportement par défaut. Vous pouvez pour cela utiliser [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] ou l'outil MageUI.exe du Kit SDK [!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)] quand vous configurez votre déploiement. Pour plus d'informations sur l'utilisation de MageUI.exe, consultez la rubrique Procédure pas à pas : déploiement d'une application ClickOnce à partir de la ligne de commande.  Consultez également [Comment : définir des autorisations personnalisées pour une application ClickOnce](http://msdn.microsoft.com/library/hafybdaa\(v=vs.110\)) ou [Comment : définir des autorisations personnalisées pour une application ClickOnce](http://msdn.microsoft.com/library/hafybdaa\(v=vs.120\)).  
  
 Pour plus d’informations sur les aspects de sécurité dans [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] et sur l’élévation d’autorisations, consultez [Déploiement et sécurité ClickOnce](/visualstudio/deployment/securing-clickonce-applications). Pour plus d’informations sur le déploiement d’applications approuvées, consultez [Vue d’ensemble du déploiement d’applications approuvées](/visualstudio/deployment/trusted-application-deployment-overview).  
  
### <a name="testing-the-application"></a>Test de l'application  
 Si vous avez déployé votre application Windows Forms à l'aide de [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], vous pouvez activer le débogage avec confiance partielle ou un jeu d'autorisations restreint à partir de l'environnement de développement.  Consultez également [Comment : déboguer une application ClickOnce avec des autorisations restreintes](http://msdn.microsoft.com/library/593zkfdf\(v=vs.110\)) ou [Comment : déboguer une application ClickOnce avec des autorisations restreintes](http://msdn.microsoft.com/library/593zkfdf\(v=vs.120\)).  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité de Windows Forms](../../../docs/framework/winforms/windows-forms-security.md)  
 [Notions fondamentales de la sécurité d’accès du code](../../../docs/framework/misc/code-access-security-basics.md)  
 [Sécurité et déploiement ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment)  
 [Vue d’ensemble du déploiement d’applications approuvées](/visualstudio/deployment/trusted-application-deployment-overview)  
 [Mage.exe (outil Manifest Generation and Editing)](../../../docs/framework/tools/mage-exe-manifest-generation-and-editing-tool.md)  
 [MageUI.exe (outil Manifest Generation and Editing, client graphique)](../../../docs/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)
