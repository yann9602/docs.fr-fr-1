---
title: "Temps de d&#233;marrage d&#39;une application | Microsoft Docs"
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
  - "démarrage d'une application (WPF)"
  - "performance (WPF), temps de démarrage"
  - "écran de démarrage (WPF), temps de démarrage"
  - "temps de démarrage (WPF)"
  - "WPF, temps de démarrage"
ms.assetid: f0ec58d8-626f-4d8a-9873-c20f95e08b96
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Temps de d&#233;marrage d&#39;une application
La durée requise pour qu'une application WPF démarre peut considérablement varier.  Cette rubrique décrit différentes techniques permettant de réduire les temps de démarrage perçus et réels pour une application Windows Presentation Foundation \(WPF\).  
  
## Fonctionnement du démarrage à froid et du démarrage à chaud  
 Le démarrage à froid se produit lorsque votre application démarre pour la première fois après un redémarrage du système, ou lorsque vous démarrez votre application, que vous la fermez, puis que vous la redémarrez après un long moment.  Lorsqu'une application démarre, si les pages requises \(code, données statiques, Registre, etc.\) ne sont pas présentes dans la liste des pages en attente du gestionnaire de mémoire Windows, des erreurs de page se produisent.  L'accès au disque est requis pour mettre les pages en mémoire.  
  
 Le démarrage à chaud se produit lorsque la plupart des pages correspondant aux composants CLR \(Common Language Runtime\) principaux sont déjà chargées en mémoire, ce qui économise un temps d'accès au disque coûteux.  C'est pourquoi une application managée démarre plus vite lorsqu'elle s'exécute pour la deuxième fois.  
  
## Implémenter un écran de démarrage  
 Dans les cas où il y a un délai inévitable relativement long entre le démarrage d'une application et l'affichage de la première interface utilisateur, optimisez le temps de démarrage perçu à l'aide d'un *écran de démarrage*.  Cette approche affiche une image presque immédiatement après le démarrage de l'application par l'utilisateur.  Lorsque l'application est prête à afficher sa première interface utilisateur, l'écran de démarrage disparaît en fondu.  À partir de [!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)], vous pouvez utiliser la classe <xref:System.Windows.SplashScreen> pour implémenter un écran de démarrage.  Pour plus d'informations, consultez [Ajouter un écran de démarrage dans une application WPF](../../../../docs/framework/wpf/app-development/how-to-add-a-splash-screen-to-a-wpf-application.md).  
  
 Vous pouvez également implémenter votre propre écran de démarrage en utilisant des graphiques Win32 natifs.  Affichez votre implémentation avant l'appel à la méthode <xref:System.Windows.Application.Run%2A>.  
  
## Analyser le code de démarrage  
 Déterminez la raison pour laquelle un démarrage à froid est lent.  L'E\/S de disque peut en être la cause, mais ce n'est pas toujours le cas.  En général, vous devez réduire l'utilisation de ressources externes, telles qu'un réseau, des services Web ou un disque.  
  
 Avant d'effectuer un test, vérifiez qu'aucune autre application ou qu'aucun autre service en cours d'exécution utilise du code managé ou du code WPF.  
  
 Démarrez votre application WPF immédiatement après un redémarrage, puis déterminez le temps nécessaire à son affichage.  Si tous les lancements suivants de votre application \(démarrage à chaud\) sont beaucoup plus rapides, l'E\/S est la cause la plus probable de votre problème de démarrage à froid.  
  
 Si le problème de démarrage à froid de votre application n'est pas lié à l'E\/S, il est probable que votre application exécute une opération d'initialisation ou de calcul longue, qu'elle attend qu'un événement se termine ou qu'elle requiert beaucoup de compilation JIT au démarrage.  Les sections suivantes décrivent certaines de ces situations plus en détail.  
  
## Optimiser le chargement de modules  
 Utilisez des outils tels que Process Explorer \(Procexp.exe\) et Tlist.exe pour déterminer quels modules sont chargés par votre application.  La commande `Tlist <pid>` affiche tous les modules chargés par un processus.  
  
 Par exemple, si vous voyez que System.Web.dll est chargé alors que vous ne vous connectez pas au Web, c'est qu'un module de votre application référence cet assembly.  Vérifiez que cette référence est nécessaire.  
  
 Si votre application comporte plusieurs modules, fusionnez\-les dans un module unique.  Cette approche requiert moins de traitement de chargement d'assemblys CLR.  Moins d'assemblys signifie également moins de maintenance de l'état par le CLR.  
  
## Différer les opérations d'initialisation  
 Envisagez de différer le code d'initialisation jusqu'à ce que la fenêtre d'application principale soit rendue.  
  
 Sachez que l'initialisation peut être exécutée à l'intérieur d'un constructeur de classe, et que si le code d'initialisation référence d'autres classes, il peut provoquer un effet de cascade dans lequel de nombreux constructeurs de classe sont exécutés.  
  
## Éviter la configuration de l'application  
 Évitez, si possible, la configuration de l'application.  Par exemple, si une application a des conditions de configuration requises simples et des objectifs de temps de démarrage stricts, des entrées de Registre ou un fichier INI simple peuvent être une alternative plus rapide pour le démarrage.  
  
## Utiliser le GAC  
 Si un assembly n'est pas installé dans le Global Assembly Cache \(GAC\), la vérification du hachage des assemblys avec nom fort et la validation des images Ngen si une image native de cet assembly est disponible sur l'ordinateur provoquent des délais.  La vérification avec nom fort est ignorée pour tous les assemblys installés dans le GAC.  Pour plus d'informations, consultez [Gacutil.exe \(outil Global Assembly Cache\)](../../../../docs/framework/tools/gacutil-exe-gac-tool.md).  
  
## Utiliser Ngen.exe  
 Si possible, utilisez Native Image Generator \(Ngen.exe\) sur votre application.  L'utilisation de Ngen.exe équivaut à favoriser l'accès au disque, aux dépends de la consommation processeur, car l'image native générée par Ngen.exe est probablement plus grande que l'image MSIL.  
  
 Pour améliorer le temps de démarrage à chaud, vous devez toujours utiliser Ngen.exe sur votre application, car cela évite le coût UC de compilation JIT du code d'application.  
  
 Il peut également être utile d'utiliser Ngen.exe dans certains scénarios de démarrage à froid.  En effet, le compilateur JIT \(mscorjit.dll\) n'a pas besoin d'être chargé.  
  
 La présence des deux modules Ngen et JIT peut avoir le pire effet.  En effet, mscorjit.dll doit être chargé, et lorsque le compilateur JIT travaille sur votre code, la lecture des métadonnées des assemblys par le compilateur JIT requiert un accès à de nombreuses pages des images Ngen.  
  
### Ngen et ClickOnce  
 La façon dont vous projetez de déployer votre application peut également faire une différence pendant le  chargement.  Le déploiement d'applications [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] ne prend pas en charge Ngen.  Si vous décidez d'utiliser Ngen.exe pour votre application, vous devrez utiliser un autre mécanisme de déploiement, tel que Windows Installer.  
  
 Pour plus d'informations, consultez [Ngen.exe \(Native Image Generator\)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md).  
  
### Redéfinition et collisions d'adresses de DLL  
 Si vous utilisez Ngen.exe, sachez qu'une redéfinition peut se produire lorsque les images natives sont chargées en mémoire.  Si une DLL n'est pas chargée à son adresse de base par défaut car cette plage d'adresses est déjà allouée, le chargeur de Windows la chargera à une autre adresse, mais cette opération peut prendre du temps.  
  
 Vous pouvez utiliser l'outil Virtual Address Dump \(Vadump.exe\) pour vérifier s'il y a des modules dans lesquels toutes les pages sont privées.  Si tel est le cas, le module a peut\-être été redéfini à une adresse différente.  Par conséquent, ses pages ne peuvent pas être partagées.  
  
 Pour plus d'informations sur la définition de l'adresse de base, consultez [Ngen.exe \(Native Image Generator\)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md).  
  
## Optimiser Authenticode  
 La vérification Authenticode s'ajoute au temps de démarrage.  Les assemblys signés avec une signature Authenticode doivent être vérifiés avec l'autorité de certification.  Cette vérification peut prendre du temps, car elle peut requérir une connexion au réseau à plusieurs reprises pour télécharger les listes de révocation de certificats actuelles.  Elle s'assure également qu'il y a une chaîne complète de certificats valides sur le chemin d'accès à une racine approuvée.  Cela peut se traduire par plusieurs secondes de délai pendant le chargement de l'assembly.  
  
 Prévoyez d'installer le certificat d'autorité de certification sur l'ordinateur client, ou évitez d'utiliser Authenticode lorsque c'est possible.  Si vous savez que votre application n'a pas besoin de la preuve d'éditeur, il n'est pas nécessaire de payer le coût de la vérification de signature.  
  
 À partir de [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)], vous disposez d'une option de configuration qui permet d'ignorer la vérification Authenticode.  Pour ce faire, ajoutez le paramètre suivant au fichier app.exe.config :  
  
```  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>   
    </runtime>  
</configuration>  
```  
  
 Pour plus d'informations, consultez [\<generatePublisherEvidence\>, élément](../../../../docs/framework/configure-apps/file-schema/runtime/generatepublisherevidence-element.md).  
  
## Comparer les performances sur Windows Vista  
 Le gestionnaire de mémoire de Windows Vista dispose d'une technologie appelée SuperFetch.  SuperFetch analyse les modèles d'utilisation de la mémoire dans le temps afin de déterminer le contenu de mémoire optimal pour un utilisateur spécifique.  Il fonctionne en continu de façon à gérer ce contenu à tout moment.  
  
 Cette approche diffère de la technique de prérécupération utilisée dans Windows XP, laquelle précharge les données dans la mémoire sans analyser les modèles d'utilisation.  Avec le temps, si l'utilisateur utilise fréquemment votre application WPF sur Windows Vista, le temps de démarrage à froid de votre application peut s'améliorer.  
  
## Utiliser efficacement les domaines d'application \(AppDomains\)  
 Si possible, chargez les assemblys dans une zone de code indépendante du domaine pour vous assurer que l'image native, le cas échéant, est utilisée dans tous les domaines d'application \(AppDomains\) créés dans l'application.  
  
 Pour optimiser les performances, appliquez une communication interdomaine efficace en réduisant les appels interdomaines.  Lorsque cela est possible, utilisez des appels sans arguments ou avec des arguments de type primitif.  
  
## Utiliser NeutralResourcesLanguageAttribute  
 Utilisez <xref:System.Resources.NeutralResourcesLanguageAttribute> pour spécifier la culture neutre pour <xref:System.Resources.ResourceManager>.  Cette approche évite des recherches d'assemblys qui échouent.  
  
## Utiliser la classe BinaryFormatter pour la sérialisation  
 Si vous devez utiliser la sérialisation, utilisez la classe <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> plutôt que la classe <xref:System.Xml.Serialization.XmlSerializer>.  La classe <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> est implémentée dans la bibliothèque de classes de base \(BCL\) de l'assembly mscorlib.dll.  La classe <xref:System.Xml.Serialization.XmlSerializer> est implémentée dans l'assembly System.Xml.dll, qui peut être une DLL supplémentaire à charger.  
  
 Si vous devez utiliser la classe <xref:System.Xml.Serialization.XmlSerializer>, vous pouvez obtenir de meilleures performances en prégénérant l'assembly de sérialisation.  
  
## Configurer ClickOnce pour vérifier la disponibilité de mises à jour après le démarrage  
 Si votre application utilise [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)], évitez l'accès réseau au démarrage en configurant [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] pour qu'il vérifie la disponibilité de mises à jour sur le site de déploiement après le démarrage de l'application.  
  
 Si vous utilisez le modèle de l'application du navigateur XAML \(XBAP\), n'oubliez pas que [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] vérifie la disponibilité de mises à jour sur le site de déploiement même si le XBAP se trouve déjà dans la cache [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)].  Pour plus d'informations, consultez [Sécurité et déploiement ClickOnce](../Topic/ClickOnce%20Security%20and%20Deployment.md).  
  
## Configurer le service PresentationFontCache pour qu'il démarre automatiquement  
 La première application WPF qui s'exécute après un redémarrage est le service PresentationFontCache.  Ce service met en cache les polices système, permet un meilleur accès aux polices et améliore les performances générales.  Le démarrage du service implique une charge mémoire. Par conséquent, dans certains environnements contrôlés, envisagez de configurer ce service pour qu'il démarre automatiquement lorsque le système redémarre.  
  
## Définir la liaison de données par programmation  
 Au lieu d'utiliser le XAML pour définir <xref:System.Windows.FrameworkElement.DataContext%2A> de manière déclarative pour la fenêtre principale, définissez\-le plutôt par programmation dans la méthode <xref:System.Windows.Application.OnActivated%2A>.  
  
## Voir aussi  
 <xref:System.Windows.SplashScreen>   
 <xref:System.AppDomain>   
 <xref:System.Resources.NeutralResourcesLanguageAttribute>   
 <xref:System.Resources.ResourceManager>   
 [Ajouter un écran de démarrage dans une application WPF](../../../../docs/framework/wpf/app-development/how-to-add-a-splash-screen-to-a-wpf-application.md)   
 [Ngen.exe \(Native Image Generator\)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md)   
 [\<generatePublisherEvidence\>, élément](../../../../docs/framework/configure-apps/file-schema/runtime/generatepublisherevidence-element.md)