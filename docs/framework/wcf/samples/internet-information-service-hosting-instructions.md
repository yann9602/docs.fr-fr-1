---
title: "Instructions relatives à l'hébergement dans les Services Internet (IIS)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 959a21c8-9d9d-4757-b255-4e57793ae9d6
caps.latest.revision: "30"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: de7dc897aa435d62c04c2e6a3ca82adf3a637a2a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="internet-information-service-hosting-instructions"></a>Instructions relatives à l'hébergement dans les Services Internet (IIS)
Pour exécuter les exemples hébergés par les services IIS (Internet Information Services), vous devez vous assurer que les services IIS sont correctement installés et en cours d'exécution.  
  
### <a name="to-install-iis-version-75-on-windows-server-2008-r2"></a>Pour installer IIS version 7.5 sur Windows Server 2008 R2  
  
1.  À partir de **le Gestionnaire de serveur**, sélectionnez **rôles.** Sous **résumé des rôles**, cliquez sur **ajouter des rôles**.  
  
2.  Cliquez sur **suivant** pour afficher les **sélectionner des rôles de serveur** boîte de dialogue.  
  
3.  Sélectionnez **serveur d’applications** à partir de la **rôles** liste, puis cliquez sur **suivant** à deux reprises pour afficher le **sélectionner les Services de rôle** boîte de dialogue pour le Rôle de serveur d’applications.  
  
4.  Sélectionnez le **serveur Web (IIS)** case à cocher. Si vous êtes invité à installer les services de rôle supplémentaires et des fonctionnalités, cliquez sur **ajouter les fonctionnalités requises**. Cliquez sur **suivant** à deux reprises pour afficher le **sélectionner les Services de rôle** boîte de dialogue pour le rôle serveur Web (IIS).  
  
5.  Développez **outils de gestion**, puis développez **IIS 6 Management Compatibility**. Sélectionnez **outils de script 6 IIS**. Si vous êtes invité à installer les services de rôle supplémentaires et des fonctionnalités, cliquez sur **ajouter des Services de rôle requis**. Cliquez sur **Suivant**.  
  
6.  Si l’aperçu des sélections est correct, cliquez sur **installer**.  
  
7.  Lorsque l’installation est terminée, cliquez sur **fermer**.  
  
### <a name="to-install-iis-version-75-on-windows-7"></a>Pour installer IIS version 7.5 sur Windows 7  
  
1.  Cliquez sur **Démarrer**, puis cliquez sur **le panneau de configuration**.  
  
2.  Ouvrez le **programmes** groupe.  
  
3.  Sous **programmes et fonctionnalités**, cliquez sur **activer ou désactiver des fonctionnalités Windows**.  
  
4.  Le **contrôle de compte d’utilisateur** boîte de dialogue s’affiche. Cliquez sur **Continuer**.  
  
5.  Le **des fonctionnalités Windows** boîte de dialogue s’affiche. Développez l’élément **Internet Information Services**.  
  
6.  Développez l’élément **Services World Wide Web**.  
  
7.  Développez l’élément **fonctionnalités de développement d’applications**.  
  
8.  Assurez-vous que les éléments suivants sont sélectionnés :  
  
    1.  **Extensibilité .NET**  
  
    2.  **ASP.NET**  
  
    3.  **Extensions ISAPI**  
  
    4.  **Filtres ISAPI**  
  
9. Sous l’élément **Services World Wide Web**, développez **fonctionnalités Http communes**.  
  
10. Assurez-vous que **contenu statique** est sélectionnée.  
  
11. Sous l’élément **Services World Wide Web**, développez **sécurité**.  
  
12. Assurez-vous que **l’authentification Windows** est sélectionnée.  
  
13. Sous le **Internet Information Services** directory, développez l’élément **outils d’administration Web**, puis sélectionnez **Console de gestion IIS**.  
  
14. Développez l’élément **IIS 6 Management Compatibility**, puis sélectionnez **outils de script IIS 6**.  
  
15. Sous le **Internet Information Services** directory, développez l’élément **Microsoft .NET Framework 3.5.1**, puis sélectionnez **Activation Http de Windows Communication Foundation**.  
  
16. Cliquez sur **OK**.  
  
### <a name="to-install-iis-version-70-on-windows-server-2008"></a>Pour installer IIS version 7.0 sur Windows Server 2008  
  
1.  À partir de **le Gestionnaire de serveur**, sélectionnez **rôles**. Sous **résumé des rôles**, cliquez sur **ajouter des rôles**.  
  
2.  Cliquez sur **suivant** pour afficher les **sélectionner des rôles de serveur** boîte de dialogue.  
  
3.  Sélectionnez **serveur d’applications** à partir de la **rôles** liste, puis cliquez sur **suivant** à deux reprises pour afficher le **sélectionner les Services de rôle** boîte de dialogue pour le Rôle de serveur d’applications.  
  
4.  Sélectionnez **serveur Web (IIS)** case à cocher. Si vous êtes invité à installer les services de rôle supplémentaires et des fonctionnalités, cliquez sur **ajouter les fonctionnalités requises**. Cliquez sur **suivant** à deux reprises pour afficher le **sélectionner les Services de rôle** boîte de dialogue pour le rôle serveur Web (IIS).  
  
5.  Développez **outils de gestion**, puis développez **IIS 6 Management Compatibility**. Sélectionnez **outils de script 6 IIS**. Si vous êtes invité à installer les services de rôle supplémentaires et des fonctionnalités, cliquez sur **ajouter des Services de rôle requis**. Cliquez sur **Suivant**.  
  
6.  Si l’aperçu des sélections est correct, cliquez sur **installer**.  
  
7.  Lorsque l’installation est terminée, cliquez sur **fermer**.  
  
### <a name="to-install-iis-version-70-on-windows-vista"></a>Pour installer IIS version 7.0 sur Windows Vista  
  
1.  Cliquez sur Démarrer, puis sur Panneau de configuration.  
  
2.  Sélectionnez le **programmes** groupe.  
  
3.  Sous **programmes et fonctionnalités**, cliquez sur **activer ou désactiver des fonctionnalités Windows**.  
  
4.  Le **contrôle de compte d’utilisateur** boîte de dialogue s’affiche. Cliquez sur **Continuer**.  
  
5.  Le **des fonctionnalités Windows** boîte de dialogue s’affiche. Développez l’élément **Internet Information Services**.  
  
6.  Développez l’élément **Services World Wide Web**.  
  
7.  Développez l’élément **fonctionnalités de développement d’applications**.  
  
8.  Assurez-vous que les éléments suivants sont sélectionnés :  
  
    1.  **Extensibilité .NET**  
  
    2.  **ASP.NET**  
  
    3.  **Extensions ISAPI**  
  
    4.  **Filtres ISAPI**  
  
9. Développez l’élément **outils d’administration Web**, puis sélectionnez **Console de gestion IIS**.  
  
10. Sous l’élément **Services World Wide Web**, développez **fonctionnalités Http communes**.  
  
11. Assurez-vous que **contenu statique** est sélectionnée.  
  
12. Sous l’élément **Services World Wide Web**, développez **sécurité**.  
  
13. Assurez-vous que **l’authentification Windows** est sélectionnée.  
  
14. Développez l’élément **IIS 6 Management Compatibility**, puis sélectionnez **outils de script IIS 6**.  
  
15. Développez l’élément **Microsoft .NET Framework 3.0**, puis sélectionnez **Activation Http de Windows Communication Foundation**.  
  
16. Cliquez sur**OK**.  
  
### <a name="to-install-iis-version-60-on-windows-server-2003"></a>Pour installer IIS version 6.0 sur Windows Server 2003  
  
1.  À partir de **gérer votre serveur**, cliquez sur **ajouter ou supprimer un rôle**, puis cliquez sur **suivant**.  
  
2.  Sélectionnez **serveur d’applications (IIS, ASP.NET)** à partir de la **rôle serveur** liste, puis cliquez sur **suivant**.  
  
3.  Sélectionnez **activer ASP.NET** case à cocher, puis cliquez sur **suivant**.  
  
4.  Si l'aperçu des sélections est correct, cliquez sur Suivant.  
  
### <a name="to-install-iis-version-51-on-windows-xp-with-service-pack-2-and-service-pack-3-installed"></a>Pour installer IIS version 5.1 sur Windows XP avec Service Pack 2 et Service Pack 3 installés  
  
1.  Dans le panneau de configuration, cliquez sur **Ajout / Suppression de programmes**.  
  
2.  Dans le **Ajout / Suppression de programmes** boîte de dialogue, cliquez sur **ajouter/supprimer des composants Windows**.  
  
3.  Dans le **Assistant Composants de Windows**, sélectionnez le **Internet Information Services (IIS)** case à cocher, puis cliquez sur **suivant**.  
  
4.  Si le **fichiers nécessaires** boîte de dialogue s’affiche, insérez le disque d’installation de système d’exploitation, accédez au dossier i386, puis cliquez sur **OK**.  
  
5.  Lorsque l’installation est terminée, cliquez sur **Terminer**.  
  
6.  Fermer le **Ajout / Suppression de programmes** boîte de dialogue et fermez **le panneau de configuration**.  
  
### <a name="to-verify-the-installation-of-iis-and-aspnet"></a>Pour vérifier l'installation d'IIS et d'ASP.NET  
  
1.  Enregistrez le fichier HTML indiqué à la fin de cette rubrique dans le répertoire \InetPub\wwwroot racine et nommez-le Default.aspx.  
  
2.  Ouvrez une nouvelle fenêtre de navigateur.  
  
3.  Type `http://localhost/Default.aspx` dans la zone d’adresse et appuyez sur ENTRÉE.  
  
4.  Une page web contenant le texte « Hello World » doit apparaître.  
  
> [!NOTE]
>  Chaque fois que vous installez une nouvelle version du [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], vous devez réinscrire aspnet_isapi comme extension de service Web pour IIS. Pour ce faire, émettez la commande `aspnet_regiis –I –enable`.  
  
## <a name="sample-code"></a>Exemple de code  
  
```xml  
<html>  
   <body>  
       <form >  
           <h3> Hello World  
           </h3>  
       </form>  
   </body>  
</html>  
```
