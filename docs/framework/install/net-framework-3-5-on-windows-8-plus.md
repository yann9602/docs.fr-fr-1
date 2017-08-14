---
title: "Installer .NET Framework 3.5 sur Windows 8, Windows 8.1 et Windows 10"
ms.date: 05/26/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
helpviewer_keywords:
- .NET Framework 3.5, installing on Windows 8
- Windows 8, installing .NET Framework 3.5
ms.assetid: 3eab3eb4-4573-42ac-98f8-36fb2c22c7d5
caps.latest.revision: 69
author: mairaw
ms.author: mairaw
ms.translationtype: HT
ms.sourcegitcommit: 20b0c1b36f705deb2f46ef4ab23653f829faf7ca
ms.openlocfilehash: 8a0395e28c01363eed27f327ea623feb4832c844
ms.contentlocale: fr-fr
ms.lasthandoff: 08/08/2017

---

# <a name="install-the-net-framework-35-on-windows-8-windows-81-and-windows-10"></a>Installer .NET Framework 3.5 sur Windows 8, Windows 8.1 et Windows 10

Le .NET Framework fait partie intégrante de nombreuses applications s’exécutant sur Windows et fournit des fonctionnalités communes pour l’exécution de ces applications. Pour les développeurs, le .NET Framework propose un modèle de programmation cohérent pour la création d’applications. Si vous utilisez le système d’exploitation Windows, le .NET Framework est peut-être déjà installé sur votre ordinateur. Plus précisément, [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] est fourni avec [!INCLUDE[win8](../../../includes/win8-md.md)], [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] est fourni avec [!INCLUDE[win81](../../../includes/win81-md.md)] et [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] est fourni avec Windows 10.  
  
Toutefois, .NET Framework 3.5 n’est pas automatiquement installé avec [!INCLUDE[win8](../../../includes/win8-md.md)], [!INCLUDE[win81](../../../includes/win81-md.md)] ou Windows 10, et doit être activé séparément pour exécuter des applications qui dépendent de lui. Cela doit s'effectuer Windows Update, qui est appelé de trois façons différentes. Elles requièrent toutes une connexion Internet :  
  
- [Installer .NET Framework 3.5 à la demande](#OnDemand)  
  
- [Activer .NET Framework 3.5 dans le Panneau de configuration](#ControlPanel)  
  
- [Télécharger le programme d’installation de .NET Framework 3.5](http://www.microsoft.com/en-us/download/details.aspx?id=21) (Remarque : Cette opération ne télécharge pas directement le .NET Framework ; il s’agit d’un programme d’installation qui appelle Windows Update.)  
  
Pendant l’installation, si vous rencontrez l’erreur 0x800f0906, 0x800f0907 ou 0x800f081f, consultez [Erreur d’installation de .NET Framework 3.5 : 0x800f0906, 0x800f0907 ou 0x800f081f](https://support.microsoft.com/en-us/kb/2734782). Notez qu’elles peuvent être résolues en installant la [mise à jour de sécurité 3005628](https://support.microsoft.com/kb/3005628).  
  
Si l’une des méthodes ci-dessus échoue ou que vous n’avez pas de connexion Internet, vous devez utiliser votre support d’installation Windows. Pour plus d’informations, consultez la méthode 3 mentionnée pour l’erreur 0x800f0906 dans l’ [article relatif aux erreurs d’installation de .NET Framework 3.5](https://support.microsoft.com/en-us/kb/2734782). Si vous n’avez pas de support d’installation, consultez [Créer un support d’installation pour Windows 8.1](http://windows.microsoft.com/en-US/windows-8/create-reset-refresh-media?woldogcb=0).  
  
**Remarques importantes :**
  
- En règle générale, ne désinstallez pas les versions du .NET Framework de votre ordinateur. Différentes applications dépendent de différentes versions du framework et plusieurs versions du .NET Framework peuvent coexister sur un seul ordinateur en même temps.  
  
- .NET Framework 3.5 est également utilisé par les applications conçues pour les versions 2.0 et 3.0.  
  
- Si vous installez un module linguistique Windows avant d'installer .NET Framework 3.5, l'installation de .NET Framework 3.5 risque d'échouer. Installez .NET Framework 3.5 avant d'installer tous les modules linguistiques Windows.  
  
- Windows CardSpace n'est pas disponible avec .NET Framework 3.5 sur [!INCLUDE[win8](../../../includes/win8-md.md)].  
  
- En raison de complications liées à l’installation de .NET Framework 3.5, il n’est malheureusement pas possible de fournir un programme d’installation autonome distinct pouvant s’exécuter indépendamment de Windows Update. Si toutes les autres méthodes échouent, vous devez recourir au support d’installation, comme décrit précédemment.  
  
<a name="OnDemand"></a>   
## <a name="install-the-net-framework-35-on-demand"></a>Installer .NET Framework 3.5 à la demande

Si une application nécessite .NET Framework 3.5 et qu’elle ne trouve pas cette version sur votre ordinateur, elle affiche la zone de message suivante pendant l’installation ou quand vous exécutez l’application pour la première fois. Dans la zone de message, choisissez **Installer cette fonctionnalité** pour activer .NET Framework 3.5. Cette option requiert une connexion Internet.  
  
![Boîte de dialogue pour l’installation 3.5 sur Windows 8](../../../docs/framework/deployment/media/installdialog.png "installdialog")  
  
<a name="ControlPanel"></a>   
## <a name="enable-the-net-framework-35-in-control-panel"></a>Activer .NET Framework 3.5 dans le Panneau de configuration

Vous pouvez activer .NET Framework 3.5 dans le Panneau de configuration. Cette option requiert une connexion Internet.  
  
1. Appuyez sur la touche Windows ![logo Windows](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") de votre clavier. Tapez « Fonctionnalités Windows » et appuyez sur Entrée. La boîte de dialogue **Activer ou désactiver des fonctionnalités Windows** apparaît. Vous pouvez aussi ouvrir le Panneau de configuration, cliquer sur les éléments de **Programmes**, puis sélectionner **Activer ou désactiver des fonctionnalités Windows** sous **Programmes et fonctionnalités**.  
  
2. Cochez la case **.NET Framework 3.5 (inclut .NET 2.0 et 3.0)**, sélectionnez **OK** et redémarrez l’ordinateur si vous y êtes invité.  
  
Vous n’avez pas besoin de sélectionner des éléments enfants pour l’**activation HTTP WCF (Windows Communication Foundation)**, sauf si vous êtes un développeur et que vous avez besoin des fonctionnalités de script WCF et de mappage de gestionnaire.
  
## <a name="see-also"></a>Voir aussi

[Guide d’installation](../../../docs/framework/get-started/index.md)

