---
title: Data Binding in an ASP.NET Client
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 68b49fa6-94e7-4d4c-a34e-902a2b3770b6
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8f7a3c4adb1a72a31029da7f73778a5ed407b2f0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="data-binding-in-an-aspnet-client"></a>Data Binding in an ASP.NET Client
Cet exemple indique comment lier des données retournées par un service [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] standard dans une application Web Forms.  
  
> [!NOTE]
>  La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
 Cet exemple contient un service qui implémente un contrat définissant un modèle de communication demande-réponse. Il se compose d'une application Web Forms cliente accessible à partir d'un navigateur, et d'un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hébergé par les services Internet (IIS).  
  
 Le service implémente un contrat qui définit un modèle de communication demande-réponse. Le contrat est défini par l'interface `IWeatherService`, laquelle expose une opération nommée `GetWeatherData`. Cette opération accepte un tableau de villes et retourne un tableau d'objets `WeatherData` qui représente les prévisions de températures maximales et minimales d'une ville.  
  
 Sur la page .aspx du client [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], un contrôle Web DataGrid est défini et contient la représentation graphique des données retournées par le service. Le code sur la page .aspx appelle le service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] et retourne les données météorologiques dans un tableau d'objets `WeatherData`. DataGrid indique où obtenir ses données en affectant ce tableau à sa propriété `DataSource`. La liaison de données se produit avec un appel à la méthode `DataBind` de DataGrid. Tout ce code est contenu dans le.`aspx` la page `Page_Load` méthode chaque fois que l’utilisateur actualise la page du navigateur, les données est mise à jour dans la grille de données.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1.  Assurez-vous d’avoir effectué la [procédure d’installation d’à usage unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Le client de cet exemple est un site Web qui s’exécute sous un serveur web de développement. Pour lancer le serveur Web de développement, tapez la commande suivante à l’invite de commande : «`%SystemDrive%\Program Files\Common Files\Microsoft Shared\DevServer\9.0\WebDev.WebServer.EXE" /port:8000 /path:<WebFormsSamplePath>\CS\client /vpath:/client`. Puis accédez à http://localhost:8000/client. Pour exécuter cet exemple sur plusieurs ordinateurs, remplacez toutes les références à `localhost` dans le fichier Web.config du client par le nom d'ordinateur du serveur.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WebForms`  
  
## <a name="see-also"></a>Voir aussi
