---
title: "Vue d&#39;ensemble des applications de navigateur XAML | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "applications hébergées par un navigateur (WPF)"
  - "applications de navigateur XAML (XBAP) WPF"
  - "applications de navigateur XAML (XBAP)"
  - "XBAP, application de navigateur XAML"
ms.assetid: 3a7a86a8-75d5-4898-96b9-73da151e5e16
caps.latest.revision: 47
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 47
---
# Vue d&#39;ensemble des applications de navigateur XAML
<a name="introduction"></a> Les [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] combinent les fonctions d'applications Web et d'applications clientes enrichies.  À l'instar des applications Web, les applications XBAP peuvent être déployées sur un serveur Web et démarrées à partir d'Internet Explorer ou de Firefox.  Comme les applications clientes enrichies, les applications XBAP peuvent bénéficier des fonctions de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Le développement d'applications XBAP est également semblable au développement de client enrichi.  Cette rubrique fournit une introduction simple, de haut niveau au développement XBAP et décrit en quoi le développement XBAP diffère du développement de client enrichi standard.  
  
 Cette rubrique contient les sections suivantes :  
  
-   [Création d'une application du navigateur XAML \(XBAP\)](#creating_a_new_xaml_browser_application_xbap)  
  
-   [Déploiement d'une application XBAP](#deploying_a_xbap)  
  
-   [Communication avec la page Web hôte](#communicating_with_the_host_web_page)  
  
-   [Considérations relatives à la sécurité XBAP](#xbap_security_considerations)  
  
-   [Considérations sur les performances relatives à la durée de démarrage de XBAP](#xbap_start_time_performance_considerations)  
  
<a name="creating_a_new_xaml_browser_application_xbap"></a>   
## Création d'une application du navigateur XAML \(XBAP\)  
 Le moyen le plus simple de créer un nouveau projet XBAP consiste à utiliser [!INCLUDE[vs_dev10_ext](../../../../includes/vs-dev10-ext-md.md)].  Lorsque vous créez un projet, sélectionnez **Application de navigateur WPF** dans la liste de modèles.  Pour plus d'informations, consultez [Comment : créer un projet d'application de navigateur WPF](http://msdn.microsoft.com/fr-fr/72ef4d90-e163-42a1-8df0-ea7ccfd1901f).  
  
 Lorsque vous exécutez le projet XBAP, il s'ouvre dans une fenêtre du navigateur au lieu de s'ouvrir dans une fenêtre autonome.  Lorsque vous déboguez l'application XBAP à partir de [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], elle s'exécute avec les autorisations de zone Internet et lèvera des exceptions de sécurité si ces autorisations sont dépassées.  Pour plus d'informations, consultez [Sécurité](../../../../docs/framework/wpf/security-wpf.md) et [Sécurité de confiance partielle de WPF](../../../../docs/framework/wpf/wpf-partial-trust-security.md).  
  
> [!NOTE]
>  Si vous ne développez pas avec [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] ou si vous voulez en savoir plus sur les fichiers projet, consultez [Génération d'une application WPF](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md).  
  
<a name="deploying_a_xbap"></a>   
## Déploiement d'une application XBAP  
 Lorsque vous générez une application XBAP, la sortie inclut les trois fichiers suivants :  
  
|Fichier|Description|  
|-------------|-----------------|  
|Fichier exécutable \(.exe\)|Celui\-ci contient le code compilé et porte une extension .exe.|  
|Manifeste d'application \(.manifest\)|Celui\-ci contient les métadonnées associées à l'application et porte une extension .manifest.|  
|Manifeste de déploiement \(.xbap\)|Ce fichier contient les informations utilisées par [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)] pour déployer l'application et a l'extension .xbap.|  
  
 Vous déployez des applications XBAP sur un serveur Web, par exemple [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] ou versions ultérieures.  Vous n'avez pas à installer le [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] sur le serveur Web, mais vous devez enregistrer les types [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)][!INCLUDE[TLA#tla_mime](../../../../includes/tlasharptla-mime-md.md)] et les extensions de noms de fichiers.  Pour plus d'informations, consultez [Configurer IIS 5.0 et IIS 6.0 pour déployer des applications WPF](../../../../docs/framework/wpf/app-development/how-to-configure-iis-5-0-and-iis-6-0-to-deploy-wpf-applications.md).  
  
 Pour préparer votre application XBAP pour le déploiement, copiez les manifestes .exe et associés sur le serveur Web.  Créez une page HTML qui contient un lien hypertexte pour ouvrir le manifeste de déploiement, qui est le fichier doté de l'extension .xbap.  Lorsque l'utilisateur clique sur le lien vers le fichier .xbap, [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] gère automatiquement la mécanique du téléchargement et le démarrage de l'application.  Le code d'exemple suivant affiche une page HTML qui contient un lien hypertexte pointant sur une application XBAP.  
  
```  
<html>   
  <head></head>  
  <body>   
    <a href="XbapEx.xbap">Click this link to launch the application</a>  
  </body>   
</html>  
  
```  
  
 Vous pouvez également héberger une application XBAP dans le frame d'une page Web.  Créez une page Web avec un ou plusieurs frames.  Affectez à la propriété source d'un frame le fichier manifeste de déploiement.  Si vous voulez utiliser le mécanisme intégré de communication entre la page Web d'hébergement et l'application XBAP, vous devez héberger l'application dans un frame.  Le code d'exemple suivant affiche une page HTML avec deux frames, la source pour le deuxième frame a la valeur d'une application XBAP.  
  
```  
<html>   
  <head>A page with frames.</head>  
    <frameset cols="50%,50%">   
      <frame src="introduction.htm" >   
      <frame src="XbapEx.xbap" >   
  </frameset>   
</html>  
```  
  
### Effacement des XBAP mis en cache  
 Dans certaines situations après avoir reconstruit et démarré votre application XBAP, vous pouvez découvrir qu'une version antérieure de l'application XBAP est ouverte.  Par exemple, ce problème peut se produire lorsque votre numéro de version d'assembly d'application XBAP est statique et que vous démarrez l'application XBAP à partir de la ligne de commande.  Dans ce cas, parce que le numéro de version entre la version mise en cache \(version démarrée précédemment\) et la nouvelle version reste le même, la nouvelle version de l'application XBAP n'est pas téléchargée.  À la place, la version mise en cache est chargée.  
  
 Dans ces situations, vous pouvez supprimer la version mise en cache à l'aide de la commande **Mage** \(installée avec Visual Studio ou le [!INCLUDE[TLA2#tla_lhsdk](../../../../includes/tla2sharptla-lhsdk-md.md)]\) à l'invite de commandes.  La commande suivante efface le cache de l'application.  
  
 `Mage.exe -cc`  
  
 Cette commande garantit que la version la plus récente de votre application XBAP est démarrée.  Lorsque vous déboguez votre application dans [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], la version la plus récente de XBAP doit être démarrée. En général, vous devez mettre à jour votre numéro de version de déploiement avec chaque build.  Pour plus d'informations sur Mage, consultez [Mage.exe \(outil Manifest Generation and Editing\)](../../../../docs/framework/tools/mage-exe-manifest-generation-and-editing-tool.md).  
  
<a name="communicating_with_the_host_web_page"></a>   
## Communication avec la page Web hôte  
 Lorsque l'application est hébergée dans un frame HTML, vous pouvez communiquer avec la page Web qui contient l'application XBAP.  Pour ce faire, vous récupérez la propriété <xref:System.Windows.Interop.BrowserInteropHelper.HostScript%2A> de <xref:System.Windows.Interop.BrowserInteropHelper>.  Cette propriété retourne un objet de script qui représente la fenêtre HTML.  Vous pouvez alors accéder aux propriétés, méthodes et événements sur l'[objet window](http://go.microsoft.com/fwlink/?LinkId=160274) en utilisant la syntaxe de point normale.  Vous pouvez également accéder aux méthodes de script et aux variables globales.  L'exemple suivant montre comment extraire l'objet de script et fermer la fenêtre du navigateur.  
  
 [!code-csharp[XbapBrowserInterop#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/xbapbrowserinterop/cs/page1.xaml.cs#10)]
 [!code-vb[XbapBrowserInterop#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/xbapbrowserinterop/vb/page1.xaml.vb#10)]  
  
### Débogage des applications XBAP qui utilisent HostScript  
 Si votre application XBAP utilise l'objet <xref:System.Windows.Interop.BrowserInteropHelper.HostScript%2A> pour communiquer avec la fenêtre HTML, il existe deux paramètres que vous devez spécifier pour faire fonctionner et déboguer l'application dans [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)].  L'application doit avoir accès à son site d'origine et vous devez la démarrer avec la page HTML qui contient l'application XBAP.  Les étapes suivantes décrivent comment vérifier ces deux paramètres :  
  
1.  Dans Visual Studio, ouvrez les propriétés du projet.  
  
2.  Sous l'onglet **Sécurité**, cliquez sur **Avancé**.  
  
     La boîte de dialogue Paramètres de sécurité avancés apparaît.  
  
3.  Assurez\-vous que la case à cocher **Autoriser l'application à accéder à son site d'origine** est activée, puis cliquez sur **OK**.  
  
4.  Sous l'onglet **Débogage**, sélectionnez l'option **Démarrer le navigateur avec l'URL** et spécifiez l'URL pour la page HTML qui contient l'application XBAP.  
  
5.  Dans Internet Explorer, cliquez sur le bouton **Outils**, puis sélectionnez **Options Internet**.  
  
     La boîte de dialogue Options Internet apparaît.  
  
6.  Cliquez sur l'onglet **Avancés**.  
  
7.  Dans la liste **Paramètres** sous **Sécurité**, activez la case à cocher **Autoriser l’exécution du contenu actif dans les fichiers de mon ordinateur**.  
  
8.  Cliquez sur **OK**.  
  
     Les modifications entreront en vigueur après que vous redémarrez Internet Explorer.  
  
> [!CAUTION]
>  Activer le contenu actif dans Internet Explorer peut présenter un risque pour votre ordinateur.  Pour plus d'informations, consultez [Fonctionnalités de sécurité et de confidentialité dans Internet Explorer](http://go.microsoft.com/fwlink/?LinkId=179286).  Si vous ne voulez pas modifier vos paramètres de sécurité Internet Explorer, vous pouvez lancer la page HTML à partir d'un serveur et attacher le débogueur [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] au processus.  
  
<a name="xbap_security_considerations"></a>   
## Considérations relatives à la sécurité XBAP  
 Les applications XBAP s'exécutent en général dans un bac à sable \(sandbox\) de sécurité de confiance partielle restreint au jeu d'autorisations de zone Internet.  Par conséquent, votre implémentation doit prendre en charge le sous\-ensemble d'éléments [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pris en charge dans la zone Internet ou vous devez élever les autorisations de votre application.  Pour plus d'informations, consultez [Sécurité](../../../../docs/framework/wpf/security-wpf.md).  
  
 Lorsque vous utilisez un contrôle <xref:System.Windows.Controls.WebBrowser> dans votre application, WPF instancie en interne le contrôle ActiveX WebBrowser natif.  Lorsque votre application est une application XBAP de confiance partielle qui fonctionne dans Internet Explorer, le contrôle ActiveX s'exécute dans un thread dédié du processus Internet Explorer.  Par conséquent, les limitations suivantes s'appliquent :  
  
-   Le contrôle <xref:System.Windows.Controls.WebBrowser> doit fournir le comportement semblable au navigateur hôte, notamment les restrictions de sécurité.  Quelques\-unes de ces restrictions de sécurité peuvent être contrôlées via les paramètres de sécurité Internet Explorer.  Pour plus d'informations, consultez [Sécurité](../../../../docs/framework/wpf/security-wpf.md).  
  
-   Une exception est levée lorsqu'une application XBAP est chargée en inter\-domaines dans une page HTML.  
  
-   L'entrée est sur un thread séparé à partir du <xref:System.Windows.Controls.WebBrowser> WPF, donc l'entrée au clavier ne peut pas être interceptée et l'état d'IME n'est pas partagé.  
  
-   Le temps ou l'ordre de navigation peut être différent en raison du contrôle ActiveX qui fonctionne sur un autre thread.  Par exemple, la navigation jusqu'à une page n'est pas toujours annulée en démarrant une autre requête de navigation.  
  
-   Un contrôle ActiveX personnalisé peut rencontrer des problèmes de communication puisque l'application WPF s'exécute dans un thread séparé.  
  
-   <xref:System.Windows.Interop.HwndHost.MessageHook> n'est pas levé parce que <xref:System.Windows.Interop.HwndHost> ne peut pas sous\-classer une fenêtre qui fonctionne dans un autre thread ou processus.  
  
### Création d'une application XBAP de confiance totale  
 Si votre application XBAP requiert une confiance totale, vous pouvez modifier votre projet pour activer cette autorisation.  Les étapes suivantes décrivent comment activer la confiance totale :  
  
1.  Dans Visual Studio, ouvrez les propriétés du projet.  
  
2.  Sous l'onglet **Sécurité**, sélectionnez l'option **Il s'agit d'une application de confiance totale**.  
  
 Ce paramètre apporte les modifications suivantes :  
  
-   Dans le fichier projet, la valeur d'élément `<TargetZone>` est modifiée par `Custom`.  
  
-   Dans le manifeste de l'application \(app.manifest\), un attribut `Unrestricted="true"` est ajouté à l'élément `PermissionSet`.  
  
    ```  
    <PermissionSet class="System.Security.PermissionSet"   
        version="1"   
        ID="Custom"   
        SameSite="site"   
        Unrestricted="true"   
    />  
    ```  
  
### Déploiement d'une application XBAP de confiance totale  
 Lorsque vous déployez une application XBAP de confiance totale qui ne suit pas le modèle de déploiement de confiance ClickOnce, son comportement lors de l'exécution par l'utilisateur dépendra de la zone de sécurité.  Dans certains cas, l'utilisateur recevra un avertissement lorsqu'il essaie de l'installer.  L'utilisateur peut choisir de continuer ou d'annuler l'installation.  Le tableau suivant décrit le comportement de l'application pour chaque zone de sécurité et ce que vous devez faire pour que l'application reçoive la confiance totale.  
  
|Zone de sécurité|Comportement|Obtention de la confiance totale|  
|----------------------|------------------|--------------------------------------|  
|Ordinateur local|Confiance totale automatique|Aucune action n'est requise.|  
|Intranet et sites approuvés|Invite pour la confiance totale|Signez le XBAP avec un certificat afin que l'utilisateur consulte la source dans l'invite.|  
|Internet|Échecs avec « Confiance non accordée »|Signez l'application XBAP avec un certificat.|  
  
> [!NOTE]
>  Le comportement décrit dans le tableau précédent concerne les applications XBAP de confiance totale qui ne suivent pas le modèle de déploiement de confiance ClickOnce.  
  
 Il est recommandé d'utiliser le modèle de déploiement de confiance ClickOnce pour le déploiement d'une application XBAP de confiance totale.  Ce modèle permet à votre application XBAP de recevoir automatiquement la confiance totale, indépendamment de la zone de sécurité, afin que l'utilisateur ne reçoive pas d'invite.  Dans le cadre de ce modèle, vous devez signer votre application à l'aide d'un certificat d'un éditeur approuvé.  Pour plus d'informations, consultez [Vue d'ensemble du déploiement d'applications approuvées](../Topic/Trusted%20Application%20Deployment%20Overview.md) et [Introduction à la signature de code \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkId=166327).  
  
<a name="xbap_start_time_performance_considerations"></a>   
## Considérations sur les performances relatives à la durée de démarrage de XBAP  
 Un aspect important de la performance de l'application XBAP est sa durée de démarrage.  Si une application XBAP est la première application WPF à être chargée, le temps de *démarrage à froid* peut durer dix secondes ou plus.  C'est parce que la page de progression est rendue par WPF, et que le CLR et WPF doivent être démarrés à froid pour afficher l'application.  
  
 En commençant dans [!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)], la durée de démarrage à froid de XBAP est atténuée en affichant une page de progression non managée tôt dans le cycle de déploiement. La page de progression s'affiche quasiment immédiatement après le lancement de l'application, car elle est affichée par le code d'hébergement natif et rendue en HTML.  
  
 De plus, un meilleur accès concurrentiel de la séquence de téléchargement [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] améliore la durée de démarrage jusqu'à dix pour cent.  Après que [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] télécharge et valide les manifestes, le téléchargement de l'application démarre et la barre de progression commence à se mettre à jour.  
  
## Voir aussi  
 [Configurer Visual Studio pour déboguer une application de navigateur XAML et appeler un service Web](../../../../docs/framework/wpf/app-development/configure-vs-to-debug-a-xaml-browser-to-call-a-web-service.md)   
 [Déploiement d'une application WPF](../../../../docs/framework/wpf/app-development/deploying-a-wpf-application-wpf.md)