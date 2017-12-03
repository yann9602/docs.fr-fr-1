---
title: "Dépannage du didacticiel de mise en route"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 69a21511-0871-4c41-9a53-93110e84d7fd
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f7372aab9e728876a6127eb49e1594ac50810c99
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="troubleshooting-the-getting-started-tutorial"></a>Dépannage du didacticiel de mise en route
Cette rubrique décrit les problèmes les plus courants rencontrés pendant l'exécution du didacticiel de prise en main et comment les résoudre.  
  
1.  [Je n’arrive pas à trouver les fichiers de projet sur mon disque dur.](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md#BKMK_q1)  
  
2.  [Tentative d'exécution de l'application de service : HTTP n'a pas pu inscrire l'URL http://+:8000/ServiceModelSamples/Service/. Le processus n'a pas de droits d'accès à cet espace de noms.](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md#BKMK_q2)  
  
3.  [Essayez d’utiliser l’outil Svcutil.exe : 'svcutil' n’est pas reconnu comme une commande interne ou externe, un programme exécutable ou un fichier de commandes.](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md#BKMK_q3)  
  
4.  [Impossible de trouver le fichier App.config généré par Svcutil.exe.](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md#BKMK_q4)  
  
5.  [La compilation de l’application cliente : 'CalculatorClient' ne contient pas de définition pour '&lt;nom de la méthode&gt;'et aucune méthode d’extension'&lt;nom de la méthode&gt;' acceptant un premier argument de type 'CalculatorClient' est introuvable (vous manque-t-il une à l’aide de la directive ou une référence d’assembly ?)](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md#BKMK_q5)  
  
6.  [La compilation de l’application cliente : le nom de type ou espace de noms 'CalculatorClient' est introuvable (vous manque-t-il une à l’aide de la directive ou une référence d’assembly ?)](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md#BKMK_q6)  
  
7.  [Le client en cours d’exécution : Exception non gérée : System.ServiceModel.EndpointNotFoundException : connexion impossible à http://localhost : 8000/ServiceModelSamples/Service/CalculatorService. Code d’erreur TCP 10061 : aucune connexion n’a pu aboutir car l’ordinateur cible l’a activement refusée.](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md#BKMK_q7)  
  
<a name="BKMK_q1"></a>   
## <a name="i-am-unable-to-find-the-project-files-on-my-hard-drive"></a>Je n'arrive pas à trouver les fichiers projet sur mon disque dur.  
 [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)]enregistre les fichiers projet dans c:\users\\< utilisateur name\Documents\\< version de Visual Studio\>\Projects dans [!INCLUDE[wv](../../../includes/wv-md.md)] et [!INCLUDE[win7_client_secondref](../../../includes/win7-client-secondref-md.md)]et c:\Documents and Settings\\< nom d’utilisateur\>\My documents\\< version de Visual Studio\>\Projects dans les versions antérieures de Windows.  
  
<a name="BKMK_q2"></a>   
## <a name="attempting-to-run-the-service-application-http-could-not-register-url-http8000servicemodelsamplesservice-your-process-does-not-have-access-rights-to-this-namespace"></a>Tentative d'exécution de l'application de service : HTTP n'a pas pu inscrire l'URL http://+:8000/ServiceModelSamples/Service/. Le processus n'a pas de droits d'accès à cet espace de noms.  
 Le processus qui héberge un service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] doit être exécuté avec les privilèges d'administrateur. Si vous exécutez le service à partir de [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)], vous devez exécuter [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] en tant qu'Administrateur. Pour cela, cliquez sur **Démarrer**, avec le bouton droit [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] et sélectionnez **exécuter en tant qu’administrateur**. Si vous exécutez le service à partir d'une invite de ligne de commande, vous devez démarrer cette invite en tant qu'administrateur de la même façon. Cliquez sur **Démarrer**, avec le bouton droit **invite de commandes** et sélectionnez **exécuter en tant qu’administrateur**.  
  
<a name="BKMK_q3"></a>   
## <a name="attempting-to-use-the-svcutilexe-tool-svcutil-is-not-recognized-as-an-internal-or-external-command-operable-program-or-batch-file"></a>Tentative d'utilisation de l'outil Svcutil.exe : 'svcutil' n'est pas reconnu en tant que commande interne ou externe, un programme exécutable ou un fichier de commandes.  
 Svcutil.exe doit figurer dans le chemin d'accès système. La solution la plus simple consiste à utiliser l'invite de commandes. Cliquez sur **Démarrer**, sélectionnez **tous les programmes**, [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)], **Visual Studio Tools**, et [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] **invite de commandes**. Cette invite de commandes affecte au chemin d'accès système les emplacements corrects de tous les outils livrés avec [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].  
  
<a name="BKMK_q4"></a>   
## <a name="unable-to-find-the-appconfig-file-generated-by-svcutilexe"></a>Impossible de trouver le fichier App.config généré par Svcutil.exe.  
 Le **ajouter un élément existant** boîte de dialogue affiche uniquement les fichiers portant les extensions suivantes par défaut : .cs, .resx, .settings, .xsd, .wsdl. Vous pouvez spécifier que vous souhaitez consulter tous les types de fichiers en sélectionnant **tous les fichiers (\*.\*)**  dans la liste déroulante dans le coin inférieur droit de la **ajouter un élément existant** boîte de dialogue.  
  
<a name="BKMK_q5"></a>   
## <a name="compiling-the-client-application-calculatorclient-does-not-contain-a-definition-for-method-name-and-no-extension-method-method-name-accepting-a-first-argument-of-type-calculatorclient-could-be-found-are-you-missing-a-using-directive-or-an-assembly-reference"></a>La compilation de l’application cliente : 'CalculatorClient' ne contient pas de définition pour '\<nom de la méthode >' et aucune méthode d’extension '\<nom de la méthode >' acceptant un premier argument de type 'CalculatorClient' est introuvable (vous êtes manquant d’un à l’aide de la directive ou une référence d’assembly ?)  
 Seules les méthodes marquées avec `ServiceOperationAttribute` sont exposées au monde extérieur. Si vous avez omis l'attribut `ServiceOperationAttribute` de l'une des méthodes dans l'interface `ICalculator`, vous obtenez ce message d'erreur lors de la compilation d'une application cliente qui appelle l'opération à laquelle manque l'attribut.  
  
<a name="BKMK_q6"></a>   
## <a name="compiling-the-client-application-the-type-or-namespace-name-calculatorclient-could-not-be-found-are-you-missing-a-using-directive-or-an-assembly-reference"></a>Compilation de l'application cliente : Le type ou le nom d'espace de noms 'CalculatorClient' est introuvable (une directive using ou une référence d'assembly est-elle manquante ?)  
 Vous obtenez cette erreur si vous n'ajoutez pas le fichier Proxy.cs ou Proxy.vb à votre projet client.  
  
<a name="BKMK_q7"></a>   
## <a name="running-the-client-unhandled-exception-systemservicemodelendpointnotfoundexception-could-not-connect-to-httplocalhost8000servicemodelsamplesservicecalculatorservice-tcp-error-code-10061-no-connection-could-be-made-because-the-target-machine-actively-refused-it"></a>Exécution du client : Exception non prise en charge : System.ServiceModel.EndpointNotFoundException : Connexion à http://localhost:8000/ServiceModelSamples/Service/CalculatorService impossible. Code d'erreur TCP 10061 : Aucune connexion n'a pu être établie car l'ordinateur cible l'a refusée activement.  
 Cette erreur se produit si vous exécutez l'application cliente sans exécuter le service.  
  
<a name="BKMK_q8"></a>   
## <a name="unhandled-exception-systemservicemodelsecuritysecuritynegotiationexception-soap-security-negotiation-with-httplocalhost8000servicemodelsamplesservicecalculatorservice-for-target-httplocalhost8000servicemodelsamplesservicecalculatorservice-failed"></a>Exception non gérée : System.ServiceModel.Security.SecurityNegotiationException : Échec de la négociation de sécurité SOAP avec « http://localhost:8000/ServiceModelSamples/Service/CalculatorService » pour la cible « http://localhost:8000/ServiceModelSamples/Service/CalculatorService »  
 Cette erreur se produit sur un ordinateur appartenant à un domaine qui ne bénéficie d'aucune connectivité réseau. Soit vous connectez votre ordinateur au réseau, soit vous désactivez la sécurité à la fois pour le client et le service. Pour le service, modifiez le code qui crée WSHttpBinding par ce qui suit.  
  
```  
// Step 3 of the hosting procedure: Add a service endpoint  
selfhost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(SecurityMode.None), "CalculatorService");  
```  
  
 Pour le client, remplacez le  **\<sécurité >** élément sous le  **\<liaison >** élément à ce qui suit :  
  
```xml  
<security mode="Node" />  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel Bien démarrer](../../../docs/framework/wcf/getting-started-tutorial.md)  
 [Démarrage rapide de la résolution des problèmes WCF](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md)  
 [Résolution des problèmes d’installation](../../../docs/framework/wcf/troubleshooting-setup-issues.md)
