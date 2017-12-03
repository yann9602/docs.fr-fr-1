---
title: Configuration de la prise en charge WS-Atomic Transaction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WS-AT protocol [WCF], configuring WS-Atomic Transaction
ms.assetid: cb9f1c9c-1439-4172-b9bc-b01c3e09ac48
caps.latest.revision: "31"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d398df112a7309979ba35020fa1d9538aa0ce5d6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="configuring-ws-atomic-transaction-support"></a>Configuration de la prise en charge WS-Atomic Transaction
Cette rubrique décrit comment configurer la prise en charge WS-AtomicTransaction (WS-AT) à l'aide de l'utilitaire de configuration WS-AT.  
  
## <a name="using-the-ws-at-configuration-utility"></a>Utilisation de l'utilitaire de configuration WS-AT  
 L'utilitaire de configuration WS-AT (wsatConfig.exe) permet de configurer les paramètres WS-AT. Pour activer le service de protocole WS-AT, vous devez utiliser l'utilitaire de configuration pour configurer le port HTTPS pour WS-AT, lier un certificat X.509 au port HTTPS et configurer des certificats de partenaire autorisés en spécifiant des noms de sujet de certificat ou des empreintes numériques. L'utilitaire de configuration vous permet également de sélectionner le mode de suivi et de définir les délais d'attente de transaction sortants et entrants maximaux par défaut.  
  
 Vous pouvez accéder aux fonctionnalités de cet outil à l'aide d'un composant logiciel enfichable de page de propriétés MMC (Microsoft Management Console) dans la console de gestion Services de composants, ou à partir d'une fenêtre de ligne de commande. Configurez la prise en charge WS-AT sur l'ordinateur local par le biais de la fenêtre de ligne de commande ; configurez les paramètres sur les ordinateurs locaux et distants à l'aide du composant logiciel enfichable MMC.  
  
 La fenêtre de ligne de commande est accessible à l'emplacement d'installation du Kit de développement logiciel (SDK) Windows « %WINDIR%\Microsoft.NET\Framework\v3.0\Windows Communication Foundation ».  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]l’outil de ligne de commande, consultez [l’utilitaire de Configuration WS-AtomicTransaction (wsatConfig.exe)](../../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md).  
  
 Si vous exécutez [!INCLUDE[wxp](../../../../includes/wxp-md.md)] ou [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], vous pouvez accéder dans le composant logiciel enfichable MMC en naviguant jusqu’au **contrôle de panneau de configuration/Administrative Tools/Services de composants**, avec le bouton droit **poste de travail**, et en sélectionnant **propriétés**. Il s’agit du même emplacement que celui où vous pouvez configurer Microsoft Distributed Transaction Coordinator (MSDTC). Les options disponibles pour la configuration sont groupées sous la **WS-AT** onglet. Si vous exécutez Windows Vista ou [!INCLUDE[lserver](../../../../includes/lserver-md.md)], le composant logiciel enfichable MMC sont accessibles en cliquant sur le **Démarrer** bouton et en entrant `dcomcnfg.exe` dans les **recherche** boîte. Lorsque la console MMC est ouverte, accédez à la **poste de travail\distributed Transaction Coordinator\Local DTC** nœud, cliquez droit et sélectionnez **propriétés**. Les options disponibles pour la configuration sont groupées sous la **WS-AT** onglet.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]les, composant logiciel enfichable, consultez le [le composant logiciel enfichable MMC de Configuration WS-AtomicTransaction](../../../../docs/framework/wcf/ws-atomictransaction-configuration-mmc-snap-in.md).  
  
 Pour activer l’interface utilisateur de l’outil, vous devez tout d’abord inscrire le fichier WsatUI.dll, qui se trouve à l’emplacement suivant  
  
 %PROGRAMFILES%\Microsoft SDKs\Windows\v6.0\Bin  
  
 Pour inscrire le produit, exécutez la commande suivante depuis une fenêtre d'invite de commandes :  
  
 `regasm.exe /codebase WsatUI.dll`  
  
## <a name="enabling-ws-at"></a>Activation de WS-AT  
 Pour activer le service de protocole WS-AT à l'intérieur de MSDTC à l'aide du port 443 et d'un certificat X.509 avec une clé privée installée dans le magasin de l'ordinateur local, utilisez l'outil wsatConfig.exe avec la commande suivante.  
  
 `WsatConfig.exe –network:enable –port:8443 –endpointCert:<machine|"Issuer\SubjectName"> -accountsCerts:<thumbprint|"Issuer\SubjectName"> -restart`  
  
 Remplacez les paramètres respectifs par des valeurs adaptées à votre environnement.  
  
 Pour désactiver le service de protocole WS-AT à l'intérieur de MSDTC, utilisez l'outil wsatConfig.exe avec la commande suivante.  
  
 `WsatConfig.exe –network:disable -restart`  
  
## <a name="configuring-trust-between-two-machines"></a>Configuration de la confiance entre deux ordinateurs  
 Le service de protocole WS-AT requiert que l'administrateur autorise explicitement les différents comptes à participer aux transactions distribuées. Si vous êtes administrateur de deux ordinateurs, vous pouvez configurer les deux ordinateurs de façon à établir une relation de confiance mutuelle en échangeant l'ensemble correct de certificats entre les ordinateurs, en les installant dans les magasins de certificats appropriés et en utilisant l'outil wsatConfig.exe pour ajouter le certificat de chaque ordinateur à la liste de certificats de participants autorisés de l'autre ordinateur. Cette étape est nécessaire pour exécuter des transactions distribuées entre deux ordinateurs à l'aide de WS-AT.  
  
 L'exemple suivant illustre les étapes requises pour établir la confiance entre deux ordinateurs, A et B.  
  
### <a name="creating-and-exporting-certificates"></a>Création et exportation de certificats  
 Cette procédure requiert le composant logiciel enfichable MMC Certificats. Ce composant logiciel enfichable est accessible en ouvrant le menu Démarrer/Exécuter, en tapant « mmc » dans la zone d'entrée et en appuyant sur OK. Puis, dans le **Console1** fenêtre, accédez à **la fichier/ajouter-supprimer** -composant logiciel enfichable, cliquez sur Ajouter et choisissez **certificats** à partir de la **autonome disponible Composants logiciels enfichables** liste. Enfin, sélectionnez **compte d’ordinateur** à gérer, puis cliquez sur **OK**. Le **certificats** nœud s’affiche dans la console du composant logiciel enfichable.  
  
 Vous devez déjà posséder les certificats requis pour établir la confiance. Pour savoir comment créer et installer de nouveaux certificats avant les étapes suivantes, consultez [Comment : créer et installer des certificats Client temporaires dans WCF pendant le développement](http://go.microsoft.com/fwlink/?LinkId=158925).  
  
1.  Sur l'ordinateur A, à l'aide du composant logiciel enfichable MMC Certificats, importez le certificat existant (certA) dans les magasins LocalMachine\MY (Nœud personnel) et LocalMachine\ROOT (nœud de l'Autorité de certification racine de confiance). Pour importer un certificat à un nœud spécifique, cliquez sur le nœud et choisissez **toutes les tâches/importer**.  
  
2.  Sur l'ordinateur B, à l'aide du composant logiciel enfichable MMC Certificats, créez ou obtenez un certificat certB avec une clé privée et importez-le dans les magasins LocalMachine\MY (Nœud personnel) et LocalMachine\ROOT (nœud de l'Autorité de certification racine de confiance).  
  
3.  Exportez la clé publique de certA dans un fichier si cela n'a pas déjà été fait.  
  
4.  Exportez la clé publique de certB dans un fichier si cela n'a pas déjà été fait.  
  
### <a name="establishing-mutual-trust-between-machines"></a>Établissement de la confiance mutuelle entre des ordinateurs  
  
1.  Sur l'ordinateur A, importez la représentation de fichier de certB dans les magasins LocalMachine\MY et LocalMachine\ROOT. Cela déclare que l'ordinateur A approuve certB pour toute communication.  
  
2.  Sur l'ordinateur B, importez le fichier certA dans les magasins LocalMachine\MY et LocalMachine\ROOT. Cela implique que l'ordinateur B approuve certA pour toute communication.  
  
 Après avoir effectué ces étapes, la confiance est établie entre les deux ordinateurs et ils peuvent être configurés pour communiquer l'un avec l'autre à l'aide de WS-AT.  
  
### <a name="configuring-msdtc-to-use-certificates"></a>Configuration de MSDTC pour utiliser des certificats  
 Le service de protocole WS-AT agissant à la fois comme client et comme serveur, il doit à la fois écouter les connexions entrantes et initier les connexions sortantes. Par conséquent, vous devez configurer MSDTC de sorte qu'il sache quel certificat utiliser lors des communications avec les correspondants externes, et quels certificats autoriser lors de l'acceptation des communications entrantes.  
  
 Vous pouvez configurer cela à l'aide du composant logiciel enfichable MMC WS-AT. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Cet outil, consultez le [le composant logiciel enfichable MMC de Configuration WS-AtomicTransaction](../../../../docs/framework/wcf/ws-atomictransaction-configuration-mmc-snap-in.md) rubrique. Les étapes suivantes décrivent comment établir la confiance entre deux ordinateurs qui exécutent MSDTC.  
  
1.  Configurez les paramètres de l'ordinateur A. Pour « Certificat de point de terminaison », sélectionnez certA. Pour « Certificats autorisés », sélectionnez certB.  
  
2.  Configurez les paramètres de l'ordinateur B. Pour « Certificat de point de terminaison », sélectionnez certB. Pour « Certificats autorisés », sélectionnez certA.  
  
> [!NOTE]
>  Lorsqu'un ordinateur envoie un message à l'autre ordinateur, l'expéditeur essaie de vérifier que le nom du sujet du certificat du destinataire et le nom d'ordinateur du destinataire correspondent. S'ils ne correspondent pas, la vérification de certificat échoue et les deux ordinateurs ne peuvent pas communiquer.  
>   
>  Pour un ordinateur joint à un domaine, le nom est le nom de domaine complet. Par défaut, le nom d'un ordinateur sur un groupe de travail est le nom NetBIOS de l'ordinateur. Toutefois, le nom peut également inclure un suffixe DNS (Domain Name System) s'il y en a un présent pour la connexion utilisée entre les deux ordinateurs.  
>   
>  Si le nom de l'ordinateur change, par exemple lorsqu'un ordinateur de groupe de travail rejoint un domaine, vous devez rééditer les certificats ou configurer manuellement les suffixes DNS.  
  
## <a name="security"></a>Sécurité  
 Étant donné que certains des paramètres liés à MSDTC et WS-AT sont stockés dans le Registre, respectivement aux emplacements HKLM\Software\Microsoft\MSDTC et HKLM\Software\Microsoft\WSAT, assurez-vous que ces clés de Registre sont sécurisées afin que seuls les administrateurs puissent y écrire. Dans l’outil Éditeur du Registre, cliquez sur la clé que vous souhaitez sécuriser et sélectionnez **autorisation** pour définir le contrôle d’accès appropriés. Il est essentiel pour la sécurité et l'intégrité du système que les clés importantes soient en lecture seule pour les utilisateurs à faible privilège.  
  
 Lors du déploiement de MSDTC, l'administrateur doit s'assurer que tout échange de données MSDTC est sécurisé. Dans un déploiement de groupe de travail, isolez l'infrastructure transactionnelle des utilisateurs malveillants ; dans un déploiement de cluster, sécurisez le Registre de cluster.  
  
## <a name="tracing"></a>Traçage  
 Le service de protocole WS-AT prend en charge intégrée, transaction suivi spécifique, qui peut être activé et géré à l’aide de la [le composant logiciel enfichable MMC de Configuration WS-AtomicTransaction](../../../../docs/framework/wcf/ws-atomictransaction-configuration-mmc-snap-in.md) outil.  Les suivis peuvent inclure des données qui indiquent l’heure d’une inscription pour une transaction spécifique, l’heure à laquelle une transaction atteint son état terminal, le résultat que chaque inscription de transaction a reçu. Toutes les traces peuvent être affichés à l’aide de la [outil Service Trace Viewer (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) outil.  
  
 Le service de protocole WS-AT prend en charge également le suivi ServiceModel intégré sur l'ensemble de la session de suivi ETW. Cela procure des suivis plus détaillés et spécifiques à la communication, en plus des suivis de transaction existants.  Pour activer ces suivis supplémentaires, procédez comme suit  
  
1.  Ouvrez le **démarrer/exécuter** menu, tapez « regedit » dans la zone d’entrée et sélectionnez **OK**.  
  
2.  Dans le **Éditeur du Registre**, accédez au dossier suivant sur le volet gauche, Hkey_Local_Machine\SOFTWARE\Microsoft\WSAT\3.0\  
  
3.  Bouton droit sur le `ServiceModelDiagnosticTracing` valeur dans le volet droit et sélectionnez **modifier**.  
  
4.  Dans le **données de la valeur** zone d’entrée, entrez une des valeurs valides suivantes pour spécifier le niveau de trace que vous souhaitez activer.  
  
-   0 : désactivé  
  
-   1 : critique  
  
-   3 : erreur. Il s'agit de la valeur par défaut  
  
-   7 : avertissement  
  
-   15 : informations  
  
-   31 : en clair  
  
## <a name="see-also"></a>Voir aussi  
 [Utilitaire de configuration WS-AtomicTransaction (wsatConfig.exe)](../../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md)  
 [Composant logiciel enfichable MMC Configuration WS-AtomicTransaction](../../../../docs/framework/wcf/ws-atomictransaction-configuration-mmc-snap-in.md)
