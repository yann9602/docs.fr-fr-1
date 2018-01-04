---
title: "Modèles Visual Studio WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a608575-3535-4190-89da-911e24c8374f
caps.latest.revision: "31"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 75723b03468c2e7aeda765f2dabfc30e394c8c88
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="wcf-visual-studio-templates"></a>Modèles Visual Studio WCF
Les modèles [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] sont des modèles d'élément et de projet prédéfinis que vous pouvez utiliser dans [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] pour générer rapidement des services [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] et des applications s'y rapportant.  
  
## <a name="using-the-wcf-templates"></a>Utilisation des modèles WCF  
 Les modèles [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] fournissent une structure de classe de base pour le développement de services. Spécifiquement, ces modèles fournissent les définitions de base pour les contrats de service, les contrats de données, les implémentations de services et les configurations. Vous pouvez utiliser ces modèles pour créer un service simple avec une interaction minimale du code, ainsi qu'un bloc de création pour des services plus avancés.  
  
### <a name="wcf-service-library-project-template"></a>Modèle de projet Bibliothèque du service WCF  
 Le [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] modèle de projet bibliothèque du Service est disponible dans la boîte de dialogue Nouveau projet sous **Visual C# \WCF** et **Visual Basic\WCF**.  
  
 Lorsque vous créez un projet à l’aide du **Service WCF** modèle, le nouveau projet inclut automatiquement les trois fichiers suivants :  
  
-   Fichier de contrat de service (IService1.cs ou IService1.vb). Le fichier de contrat de service est une interface qui possède des attributs de service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]. Ce fichier contient la définition d'un service simple destinée à vous aider à définir vos services et inclut des opérations basées des paramètres, ainsi qu'un exemple de contrat de données simple. Il s'agit du fichier par défaut qui s'affiche dans l'éditeur de code après la création d'un projet de service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].  
  
-   Fichier d'implémentation de service (Service1.cs ou Service1.vb). Le fichier d'implémentation de service implémente le contrat défini dans le fichier de contrat de service.  
  
-   Fichier de configuration de l'application (App.config). Le fichier de configuration fournit les éléments de base d'un modèle de service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] avec une liaison http sécurisée. Il inclut également un point de terminaison applicable au service et active l'échange de métadonnées.  
  
> [!NOTE]
>  [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]est configuré pour reconnaître le fichier App.config comme fichier de configuration pour le projet lorsqu’il est exécuté à l’aide de la [hôte de Service WCF (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md), qui est la configuration par défaut. Si la bibliothèque de services se trouve dans un fichier exécutable, vous devez déplacer le code de configuration vers le fichier de configuration du fichier exécutable : en effet, les fichiers de configuration des DLL ne sont pas valides.  
  
### <a name="wcf-service-application-template"></a>Modèle d'application de service WCF  
 Le [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] modèle d’Application de Service est disponible dans la boîte de dialogue Nouveau projet sous **Visual C# \WCF** et **Visual Basic\WCF**.  
  
 Lorsque vous créez un projet à l’aide du **Service d’Application Web WCF** modèle, le projet inclut les quatre fichiers suivants :  
  
-   Fichier d'hôte de service (service1.svc).  
  
-   Fichier de contrat de service (IService1.cs ou IService1.vb).  
  
-   Fichier d'implémentation de service (Service1.svc.cs ou Service1.svc.vb).  
  
-   Fichier de configuration Web (Web.config).  
  
 Le modèle crée automatiquement un site Web (à déployer dans un répertoire virtuel) et y héberge un service.  
  
### <a name="wcf-web-site-template"></a>Modèle de site web WCF  
 Le [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] modèle de Site Web est disponible dans la boîte de dialogue Nouveau projet sous **Visual C# \Web Site\WCF Service** et **Visual Basic\Web Site\WCF Service**. Cela crée les mêmes fichiers que ceux du modèle d’application de service WCF, mais les classe comme s’il s’agissait d’un site web ASP.NET. Les dossiers App_Code et App_Data sont créés.  
  
### <a name="wcf-service-item-template"></a>Modèle d'élément de service WCF  
 Le modèle d'élément de service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] est un modèle personnalisé qui permet d'ajouter rapidement des services [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] à vos projets [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] existants.  
  
 Pour utiliser ce modèle, accédez à la **l’Explorateur de solutions** volet, cliquez sur le nom de votre projet, pointez sur **ajouter**, puis cliquez sur **un nouvel élément** pour lancer le **Ajouter nouveau Élément** boîte de dialogue.  
  
 L’interface de service et les fichiers d’implémentation sont placés dans le dossier du projet racine.  
  
 Le modèle tente de fusionner la section de configuration du nouveau service avec le fichier de configuration existant, si leurs types sont compatibles.  
  
 Un fichier d'hôte de service (service1.svc) est également créé si le projet existant est un projet Web.  
  
### <a name="wcf-wf-service-project-and-item-template"></a>Modèles d'élément et de projet de service WF WCF.  
 Ces modèles créent des services [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] qui hébergent un service de workflow, dont l'accès est identique à celui d'un service Web. Différents modèles existent pour les XAML et les modèles de programmation impératifs. À l'aide des modèles, vous pouvez créer des workflows séquentiels ou des workflows de l'ordinateur d'état. Pour plus d’informations sur ces types de flux de travail, consultez [Windows Workflow Foundation didacticiels](http://msdn.microsoft.com/en-us/e9705654-bd96-4b56-8d98-f1f118112d97). [!INCLUDE[crabout](../../../includes/crabout-md.md)]créer des projets de flux de travail, consultez [création de projets de Workflow hérité](/visualstudio/workflow-designer/creating-legacy-workflow-projects).  
  
 Le concepteur [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] est plus réactif lorsque des workflows de type XOML sont utilisés au lieu de workflows basés sur le code. Le workflow XOML est le type de workflow par défaut à créer.  
  
### <a name="wcf-syndication-service-library-template"></a>Modèle de la bibliothèque du service de syndication WCF  
 Ce modèle permet d'exposer votre flux au format RSS ou ATOM en tant que service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]. Pour plus d’informations, consultez [Syndication WCF](../../../docs/framework/wcf/feature-details/wcf-syndication.md).  
  
#### <a name="changing-the-address-of-the-feed"></a>Modification de l'adresse du flux  
 Le modèle de syndication utilise Internet Explorer au cours de l'exécution. Lorsque vous cliquez sur votre projet dans **l’Explorateur de Solutions** dans [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], sélectionnez **propriétés**, puis sélectionnez le **déboguer** onglet et vous pouvez voir l’adresse par défaut le modèle. Internet Explorer tente d'ouvrir le flux à cette adresse.  
  
 Si vous modifiez l’adresse de votre flux, vous devez également modifier l’adresse dans le **déboguer** onglet. Sinon, Internet Explorer tente d'ouvrir le flux à l'adresse par défaut et échoue.  
  
### <a name="ajax-enabled-wcf-service-item-template"></a>Modèle d'élément de service WCF AJAX  
 Ce modèle expose un contrôle AJAX en tant que service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]. Pour plus d’informations sur les contrôles d’AJAX, consultez le [documentation sur le contrôle AJAX](http://go.microsoft.com/fwlink/?LinkId=96717).  
  
### <a name="silverlight-enabled-wcf-service-item-template"></a>Modèle d'élément de service WCF compatible Silverlight  
 Ce modèle crée un service Web qui fournit des données à un client Silverlight ou frontal. Il peut être ajouté à un site Web ou à un projet d'application Web pour créer un service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], qui inclut le code et la configuration du service prenant en charge la communication avec un client Silverlight. Vous pouvez ensuite utiliser **ajouter une référence de Service** pour ajouter un proxy client du service au client et échanger des données entre le client Silverlight et le service WCF compatible Silverlight.  
  
 Pour accéder à ce modèle, cliquez sur un projet d’application Web ou le site Web dans **l’Explorateur de solutions**, cliquez sur **ajouter un nouvel élément**, puis cliquez sur **Service WCF compatible Silverlight**.  
  
> [!NOTE]
>  Le service WCF compatible Silverlight expose un point de terminaison `basicHttpBinding` sans activer de paramètre de sécurité. Par conséquent, les informations concernant le service peuvent être obtenues par tous les clients qui s'y connectent. Les messages échangés entre le service et le client ne sont pas signés ni chiffrés. Pour sécuriser correctement le point de terminaison, vous devez utiliser l'authentification ASP.NET, HTTPS ou d'autres mécanismes.  
  
## <a name="see-also"></a>Voir aussi  
 [WCF Service Host (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
 [Client test WCF (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)
