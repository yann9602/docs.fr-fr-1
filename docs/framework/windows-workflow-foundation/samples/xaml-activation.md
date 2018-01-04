---
title: XAML Activation
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 486760e2-bb10-4ed5-8c02-fe7472498d2d
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 53665f39c6c0c7e5c7956912b05e3fd80659ddcb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="xaml-activation"></a>XAML Activation
Cet exemple montre comment héberger un workflow déclaratif dans IIS. C'est un workflow de base appelé `EchoService` qui comporte une opération.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez-vous sur la page de téléchargement pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\XAMLActivation`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1.  Ouvrez la solution XAMLActivation.sln dans [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Générez la solution en appuyant sur **F5**.  
  
3.  Exécutez WcfTestClient.exe. À partir d'une invite de commandes, tapez ce qui suit :  
  
    1.  cd %SystemDrive%\Program Files\Microsoft Visual Studio 10.0\Common7\IDE  
  
    2.  Exécutez WcfTestClient.exe.  
  
4.  Définissez l'adresse du service sur WcfTestClient.exe en appuyant sur CTRL+MAJ+A et en affectant à l'adresse du service la valeur http://localhost:56133/Service.xamlx.  
  
5.  Effectuez l'opération Echo pour tester le service.  
  
6.  Déployez le service dans IIS en utilisant DeployToIIS.Bat dans une invite de commandes avec des privilèges d'administrateur.  
  
7.  Mettez à jour l'adresse de service dans le client en spécifiant http://localhost/XAMLActivation/Service.xamlx et testez à nouveau le service à l'aide de WcfTestClient.exe.
