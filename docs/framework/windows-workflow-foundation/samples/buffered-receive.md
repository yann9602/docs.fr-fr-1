---
title: "Mise en mémoire tampon de la réception"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9d46d9b9-96c9-4531-9695-ab526b4d704a
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3b4851425609936d093762895cef6bdbc8ad7823
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="buffered-receive"></a>Mise en mémoire tampon de la réception
Cet exemple montre comment installer et configurer la fonctionnalité de mise en mémoire tampon de la réception dans [!INCLUDE[wf](../../../../includes/wf-md.md)]. La mise en mémoire tampon de la réception permet à l'auteur de workflow de créer un workflow sans devoir s'inquiéter de l'ordre dans lequel les messages sont reçus. La fonctionnalité de mise en mémoire tampon de la réception met les messages en mémoire tampon localement et les remet lorsque le workflow est prêt à les recevoir.  
  
## <a name="demonstrates"></a>Démonstrations  
 Traitement des messages dans le désordre à l'aide de la mise en mémoire tampon de la réception avec les activités de messagerie.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\BufferedReceive`  
  
## <a name="discussion"></a>Discussion  
 Dans cet exemple, un service [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] est implémenté à l'aide de [!INCLUDE[wf1](../../../../includes/wf1-md.md)] et a une séquence d'activités <xref:System.ServiceModel.Activities.Receive>. Ce workflow modélise un processus d'approbation d'un emprunt simple où le workflow attend trois notifications pour qu'un emprunt soit approuvé. Une application cliente [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] envoie trois notifications corrélées dans l'ordre inverse de celui attendu par le service. Étant donné que la fonctionnalité de mise en mémoire tampon de la réception est activée au niveau du service, chaque message dans le désordre est mis en mémoire tampon au niveau du service et traité lorsque le workflow est prêt à le recevoir.  
  
 La fonctionnalité de mise en mémoire tampon de la réception nécessitant la prise en charge de <xref:System.ServiceModel.Activities.ReceiveContent> à partir de la liaison, le service utilise <xref:System.ServiceModel.NetMsmqBinding>. Aucune configuration spéciale n'étant requise pour la liaison, les valeurs par défaut sont utilisées.  
  
```xml  
<endpoint address ="net.msmq://localhost/private/LoanService/Service1.xamlx"  
                  binding="netMsmqBinding"  
                  contract="ILoanService"/>  
```  
  
 Le service expose également des métadonnées pour le service à l'aide de <xref:System.ServiceModel.Description.ServiceMetadataBehavior>.  
  
 De la même façon, le point de terminaison de client est configuré à l'aide de <xref:System.ServiceModel.NetMsmqBinding>. Le code client et la configuration est généré à l’aide de la **ajouter une référence de Service** fonctionnalité de [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]. L'exemple suivant est le point de terminaison de client généré dans le fichier App.config.  
  
```xml  
<endpoint address="net.msmq://localhost/private/LoanService/Service1.xamlx"  
                binding="netMsmqBinding" bindingConfiguration="NetMsmqBinding_ILoanService"  
                contract="ServiceReference1.ILoanService" name="NetMsmqBinding_ILoanService" />  
```  
  
 Cet exemple requiert que les composants Windows suivants soient activés :  
  
1.  [!INCLUDE[iis60](../../../../includes/iis60-md.md)]  
  
2.  Compatibilité avec la gestion [!INCLUDE[iis60](../../../../includes/iis60-md.md)], Compatibilité avec la métabase et la configuration  
  
3.  Services World Wide Web, Fonctionnalités de développement d'applications et ASP.NET  
  
4.  Serveur de file d'attente Microsoft Message Queue (MSMQ)  
  
#### <a name="to-set-up-and-build-the-sample"></a>Pour configurer et générer l'exemple  
  
1.  À une invite de commandes [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], inscrivez ASP.NET en tapant `aspnet_regiis –I` et appuyez sur ENTRÉE.  
  
2.  Exécutez [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] en tant qu'administrateur.  
  
3.  Ouvrez LoanService.sln.  
  
4.  Lorsque vous êtes invité si vous souhaitez créer les répertoires virtuels pour le projet LoanService, sélectionnez **Oui**.  
  
#### <a name="to-set-up-the-service-queues"></a>Pour configurer les files d'attente de service  
  
1.  Appuyez sur F5 pour exécuter l'application LoanClient qui crée les files d'attente et active le service défini dans Service1.xamlx.  
  
2.  Ouvrez le **gestion de l’ordinateur** console en exécutant Compmgmt.msc à partir d’une invite de commandes.  
  
3.  Dans le **gestion de l’ordinateur** de la console, développez **Service**, **Applications**, **Message Queuing**, **files d’attente privées** .  
  
4.  Avec le bouton droit de la file d’attente loanservice/Service1.xamlx et sélectionnez **propriétés**.  
  
5.  Sélectionnez le **sécurité** onglet, puis ajoutez **tout le monde reçoit le Message**, **lire le Message** et **envoyer un Message** autorisations.  
  
6.  Ouvrez le Gestionnaire [!INCLUDE[iis60](../../../../includes/iis60-md.md)].  
  
7.  Accédez à **Server**, **Sites**, **site Web par défaut**, **privé**, **LoanService** et sélectionnez  **Options avancées**  
  
8.  Modifier la **protocoles activés** être **http**, **net.msmq**.  
  
#### <a name="to-run-the-sample"></a>Pour exécuter l'exemple  
  
1.  Naviguez jusqu'à http://localhost/private/loanservice/service1.xamlx pour vérifier que le service s'exécute.  
  
2.  Appuyez sur F5 pour exécuter l'application LoanClient. Une fois le workflow terminé, un fichier out.txt doit être enregistré dans C:\Inbox qui contient le résultat de l'échange de messages.  
  
#### <a name="to-clean-up"></a>Pour nettoyer  
  
1.  Ouvrez le **gestion de l’ordinateur** console en exécutant Compmgmt.msc à partir d’une invite de commandes.  
  
2.  Développez **Service** et **Applications**, **Message Queuing**, **files d’attente privées**.  
  
3.  Supprimez la file d'attente loanservice/service1.xamlx.  
  
4.  Supprimez le répertoire C:\Inbox.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\BufferedReceive`
