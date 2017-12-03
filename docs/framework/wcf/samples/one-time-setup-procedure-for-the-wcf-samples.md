---
title: "Procédure d'installation unique pour les exemples Windows Communication Foundation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a5848ffd-3eb5-432d-812e-bd948ccb6bca
caps.latest.revision: "83"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5b699a9af286287f1cdd1aa224afd3f8c41dd90d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="one-time-setup-procedure-for-the-windows-communication-foundation-samples"></a>Procédure d'installation unique pour les exemples Windows Communication Foundation
La plupart des exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] sont hébergés dans Internet Information Services (IIS) et sont exécutés à partir d'un répertoire virtuel commun. Cette procédure d’installation unique crée un dossier sur le disque ; Il ajoute également un répertoire virtuel dans IIS nommé **ServiceModelSamples**.  
  
 Le **ServiceModelSamples** répertoire virtuel est utilisé pour générer et exécuter tous les exemples qui utilisent un service hébergé par IIS. Il s'agit du seul répertoire virtuel requis pour exécuter les exemples. La génération d'un exemple remplace tout service déployé précédemment dans ce répertoire ; seul le dernier exemple généré sera déployé et disponible dans ce répertoire virtuel.  
  
> [!NOTE]
>  Vous devez exécuter toutes les commandes sous un compte d'administrateur local. Si vous utilisez Windows 7, [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)] ou Windows Server 2008 R2, vous devez également exécuter l'invite de commandes avec des privilèges élevés. Pour ce faire, cliquez sur l’icône de l’invite de commandes, puis cliquez sur **exécuter en tant qu’administrateur**. Toutes les commandes qui figurent dans cette rubrique doivent être exécutées dans une invite de commandes disposant des paramètres de chemin d’accès appropriés.  Le moyen le plus simple de vous en assurer consiste à utiliser l'invite de commandes de Visual Studio. Pour ouvrir cette invite, cliquez sur **Démarrer**, sélectionnez **tous les programmes**, faites défiler jusqu'à **Visual Studio 2010**, sélectionnez **Visual Studio Tools**, avec le bouton droit **invite de commandes Visual Studio (2010)**, puis cliquez sur **exécuter en tant qu’administrateur**. Si l’une des éditions Visual Studio Express est installée, cette invite de commandes n’est pas disponible ; il vous faut ajouter « C:\Windows\Microsoft.Net\Framework\v4.0 » au chemin d’accès système.  
  
### <a name="one-time-setup-procedure-for-wcf-samples"></a>Procédure d'installation unique pour les exemples WCF  
  
1.  Vérifiez que [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] est installé. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]comment configurer [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], consultez [Internet Information Service d’hébergement Instructions](../../../../docs/framework/wcf/samples/internet-information-service-hosting-instructions.md).  
  
2.  Vérifiez que [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] est installé. Rechercher les éléments suivants de répertoire pour la version 4.0 (ou version ultérieures) : **\Windows\Microsoft.NET\Framework**  
  
3.  Si [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] n’est pas installé, et votre système d’exploitation n’est pas Windows Server 2008 SP2 ou version ultérieure, installez [correctif 251798](http://go.microsoft.com/fwlink/?LinkId=184693).  
  
4.  Exécutez les commandes suivantes. Pour plus d’informations sur la raison pour laquelle ces commandes doivent être exécutées, consultez [IIS Service hébergé ne](http://msdn.microsoft.com/en-us/ee5499fc-1b10-4cda-a9b1-13dba70f05f8).  
  
    > [!WARNING]
    >  Si vous avez réinstallé IIS, réexécutez les commandes suivantes.  
  
    ```  
    "%WINDIR%\Microsoft.Net\Framework\v4.0.30319\aspnet_regiis" –i –enable  
    "%WINDIR%\Microsoft.Net\Framework\v4.0.30319\ServiceModelReg.exe" -r  
    ```  
  
    > [!WARNING]
    >  Exécution de la commande `aspnet_regiis –i –enable` s’exécuter le Pool d’applications par défaut à l’aide de [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], ce qui peut provoquer des problèmes d’incompatibilité pour d’autres applications sur le même ordinateur.  
  
5.  Suivez les [pare-feu Instructions](../../../../docs/framework/wcf/samples/firewall-instructions.md) pour activer les ports utilisés par les exemples.  
  
6.  Recherchez le répertoire par défaut suivant : \<Lecteurinstall > :**\WF_WCF_Samples**. Si les exemples ont été installés précédemment, il s'agit du répertoire par défaut.  
  
7.  Si les exemples ne sont pas installés, installez-les à partir de l’emplacement de téléchargement des exemples de [Visual C#](http://go.microsoft.com/fwlink/?LinkId=190939) ou [Visual Basic](http://go.microsoft.com/fwlink/?LinkID=193373).  
  
8.  Après avoir installé les exemples, accédez à : \<Lecteurinstall > :**\WF_WCF_Samples\WCF\Setup\\**  
  
9. Exécutez le **Setupvroot.bat** fichier de commandes. Les étapes suivantes sont exécutées :  
  
    -   Un répertoire virtuel, nommé ServiceModelSamples, est créé dans IIS.  
  
    -   Des répertoires de disque nommés %SystemDrive%\Inetpub\wwwroot\ServiceModelSamples et %SystemDrive%\Inetpub\wwwroot\ServiceModelSamples\bin sont créés.  
  
     Si vous préférez configurer ces répertoires manuellement, consultez le [Instructions de configuration du répertoire virtuel](../../../../docs/framework/wcf/samples/virtual-directory-setup-instructions.md). Pour annuler toutes les modifications apportées lors de cette étape, exécutez cleanupvroot.bat une fois que vous aurez terminé d'utiliser les exemples.  
  
    > [!NOTE]
    >  Cette procédure doit être effectuée une fois seulement sur un ordinateur, sauf si cleanupvroot.bat est exécuté.  
  
10. Vous devez accorder au compte utilisé pour générer les exemples et à l'utilisateur du service réseau des autorisations de modification sur le répertoire %SystemDrive%\inetpub\wwwroot. Lors de la génération, certains exemples hébergés par le Web peuvent tenter de copier les fichiers binaires compilés dans l'emplacement mentionné précédemment. Si vous n'avez pas défini les autorisations requises, leur génération échoue. Vous pouvez également laisser les autorisations telles quelles et exécuter l'invite de commandes du Kit de développement logiciel (SDK) ou de Visual Studio (2012) en tant qu'administrateur, ou générer les exemples dans [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], également en tant qu'administrateur.  
  
    > [!NOTE]
    >  Si vous ne procédez pas à cette étape, tous les exemples hébergés par IIS échouent lors de la génération. Veillez à définir les autorisations correctement ou exécutez l'invite de commandes du Kit de développement logiciel (SDK) et de Visual Studio (2012) en tant qu'administrateur.  
  
11. Créez sur l'ordinateur un répertoire C:\logs ; certains exemples peuvent en avoir besoin. Assurez-vous que le compte approprié dispose d’un accès en écriture sur ce dossier. Pour Windows 7, [!INCLUDE[wv](../../../../includes/wv-md.md)], et Windows Server 2008 R2, ce compte est **Service réseau**. Pour [!INCLUDE[lserver](../../../../includes/lserver-md.md)], le compte est Autorité NT\Service réseau. Pour [!INCLUDE[wxp](../../../../includes/wxp-md.md)] et [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], le compte est ASPNET.  
  
12. Exécutez le fichier Setupcerttool.bat. Ce fichier se trouve dans le \<Chemininstall > \WF_WCF_Samples\WCF\Setup\ dossier.  Ce script effectue les tâches suivantes :  
  
    -   génération de l'outil FindPrivateKey ;  
  
    -   création d'un répertoire nommé %ProgramFiles%\ServiceModelSampleTools ;  
  
    -   copie du nouvel outil FindPrivateKey dans ce répertoire.  
  
     Cet outil est requis pour les exemples qui utilisent des certificats et sont hébergés dans IIS.  
  
    > [!NOTE]
    >  Pour des raisons de sécurité, n'oubliez pas de supprimer la définition de répertoire virtuel et les autorisations accordées au cours des étapes d'installation ci-dessus lorsque vous en avez terminé avec les exemples en exécutant le fichier de commandes Cleanupvroot.bat.  
  
13. Les exemples auto-hébergés (non hébergés dans IIS) doivent être autorisés à enregistrer des adresses HTTP sur l'ordinateur pour pouvoir écouter les données. Ces autorisations (qui permettent de réserver les espaces de noms HTTP) dépendent directement des autorisations dont les comptes d'utilisateurs utilisés pour exécuter ces exemples disposent. Par défaut, les comptes d'administrateur sont autorisés à enregistrer n'importe quelle adresse HTTP. L'autorisation pour les espaces de noms HTTP utilisés par les exemples doit être accordée aux comptes qui ne sont pas administrateur. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]comment configurer des réservations d’espace de noms, consultez [configuration de HTTP et HTTPS](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md).  
  
14. Certains exemples nécessitent Message Queuing. Consultez [l’installation de Message Queuing (MSMQ)](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md) pour obtenir des instructions d’installation.  
  
    > [!NOTE]
    >  Veillez à démarrez le service MSMQ avant d'exécuter un exemple qui requiert Message Queuing.  
  
15. Certains exemples requièrent des certificats. Consultez [Internet Information Services (IIS) Instructions d’Installation du certificat serveur](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).  
  
## <a name="see-also"></a>Voir aussi
