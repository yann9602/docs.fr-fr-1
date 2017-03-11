---
title: "Adding Printable Reports to Visual Studio Applications | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "printing [Visual Studio], reports"
  - "reports, printing in Visual Studio"
ms.assetid: 93928405-ef41-495e-bce2-9d43d5a7080a
caps.latest.revision: 27
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 27
---
# Adding Printable Reports to Visual Studio Applications
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Visual Studio prend en charge diverses solutions de création de rapport pour vous aider à ajouter des rapports de données élaborés à vos applications Visual Basic.  Vous pouvez créer et ajouter des rapports à l'aide de contrôles ReportViewer, de Crystal Reports ou de SQL Server Reporting Services.  
  
> [!NOTE]
>  SQL Server Reporting Services fait davantage partie de SQL Server 2005 que de Visual Studio.  Reporting Services est uniquement installé sur votre système si vous avez installé SQL Server 2005.  
  
## Vue d'ensemble de la technologie de création de rapports de Microsoft dans les applications Visual Basic  
 Choisissez l'une des approches suivantes pour utiliser une technologie de création de rapports Microsoft dans votre application :  
  
-   Ajouter une ou plusieurs instances d'un contrôle ReportViewer à une application Windows Visual Basic.  
  
-   Intégrer SQL Server Reporting Services par programmation en appelant le service Web Report Server.  
  
-   Utiliser conjointement le contrôle ReportViewer et Microsoft SQL Server 2005 Reporting Services, en utilisant le contrôle comme une visionneuse de rapports et un serveur de rapports comme processeur de rapport.  \(Notez que vous devez utiliser la version SQL Server 2005 de Reporting Services si vous souhaitez utiliser conjointement un serveur de rapports et le contrôle ReportViewer\).  
  
## Utilisation de contrôles ReportViewer  
 La façon la plus simple d'incorporer les fonctionnalités de rapport dans une application Windows Visual Basic est d'ajouter le contrôle ReportViewer à un formulaire dans votre application.  Le contrôle ajoute directement des fonctions de traitement de rapports à votre application et fournit un Concepteur de rapports intégré afin que vous puissiez générer des rapports à l'aide de données provenant de n'importe quel objet de données ADO.NET.  Une API complète fournit l'accès par programmation au contrôle et aux rapports afin que vous puissiez configurer les fonctionnalités à l'exécution.  
  
 ReportViewer fournit le traitement intégré de rapports et une fonction d'affichage dans un contrôle de données unique et librement distribuable.  Choisissez des contrôles ReportViewer si vous avez besoin des fonctionnalités de rapport suivantes :  
  
-   Traitement des rapports dans l'application cliente.  Un rapport traité apparaît dans une zone d'affichage fournie par le contrôle.  
  
-   Liaison des données à des tables de données ADO.NET.  Vous pouvez créer des rapports qui utilisent des instances de <xref:System.Data.DataTable> fournies au contrôle.  Vous pouvez également créer directement une liaison à des objets métier.  
  
-   Contrôles redistribuables que vous pouvez inclure dans votre application.  
  
-   Fonctionnalités au moment de l'exécution, telles que la navigation entre les pages, l'impression, la recherche et les formats d'exportation.  Une barre d'outils ReportViewer fournit la prise en charge de ces opérations.  
  
 Pour utiliser le contrôle ReportViewer, vous pouvez le faire glisser de la section **Données** de la Boîte à outils Visual Studio vers un formulaire dans votre application Windows Visual Basic.  
  
### Création de rapports dans Visual Studio pour des contrôles ReportViewer  
 Pour générer un rapport qui s'exécute dans ReportViewer, ajoutez un modèle de **Rapport** à votre projet.  Visual Studio crée un fichier de définition de rapport client \(.rdlc\), ajoute le fichier à votre projet et ouvre un Concepteur de rapports intégré dans l'espace de travail Visual Studio.  
  
 Le Concepteur de rapports Visual Studio s'intègre dans la fenêtre **Sources de données**.  Lorsque vous faites glisser un champ de la fenêtre **Sources de données** vers le rapport, le Concepteur de rapports copie les métadonnées de la source de données dans le fichier de définition du rapport.  Ces métadonnées sont utilisées par le contrôle ReportViewer pour générer automatiquement le code de liaison de données.  
  
 Le Concepteur de rapports Visual Studio n'inclut pas de fonctionnalité d'aperçu du rapport.  Pour afficher un aperçu de votre rapport, exécutez l'application et affichez l'aperçu du rapport qu'elle contient.  
  
||  
|-|  
|Pour ajouter des fonctionnalités de rapport de base à votre application|  
|1.  Faites glisser un contrôle ReportViewer de l'onglet **Données** de la **Boîte à outils** sur votre formulaire.<br />2.  Dans le menu **Projet**, choisissez **Ajouter un nouvel élément**.  Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez l'icône **Rapport**, puis cliquez sur **Ajouter**.<br />     Le Concepteur de rapports s'ouvre dans l'environnement de développement et un fichier de rapport \(.rdlc\) est ajouté au projet.<br />3.  Faites glisser les éléments de rapport de la **Boîte à outils** vers la disposition de rapport et placez\-les comme vous le souhaitez.<br />4.  Faites glisser les champs de la fenêtre **Sources de données** vers les éléments de rapport dans la disposition de rapport.|  
  
## Utilisation de Reporting Services dans les applications Visual Basic  
 Reporting Services est une technologie de création de rapports basée sur des serveurs ; elle est incluse avec SQL Server.  Reporting Services inclut des fonctionnalités supplémentaires qui ne figurent pas dans les contrôles ReportViewer.  Choisissez Reporting Services si vous avez besoin des fonctionnalités suivantes :  
  
-   Déploiement avec montée en puissance parallèle et traitement de rapports côté serveur qui améliorent les performances des rapports complexes, longs à s'exécuter et des systèmes présentant un gros volume d'activité.  
  
-   Traitement intégré de données et de rapports, avec la prise en charge de contrôles de rapports personnalisés et de formats de sortie élaborés.  
  
-   Traitement de rapports planifié afin que vous puissiez spécifier exactement quand les rapports sont exécutés.  
  
-   Distribution de rapports à des abonnés par messagerie électronique ou sur des emplacements de partage de fichiers.  
  
-   Création de rapports ad hoc afin que les utilisateurs professionnels puissent créer des rapports selon leurs besoins.  
  
-   Abonnements pilotés par des données qui routent la sortie des rapports personnalisés vers une liste dynamique de destinataires.  
  
-   Extensions personnalisées pour le traitement de données, la remise des rapports, l'authentification personnalisée et le rendu des rapports.  
  
 Le serveur de rapports est implémenté comme service Web.  Le code de votre application doit inclure des appels au service Web pour accéder aux rapports et aux autres métadonnées.  Le service Web fournit l'accès complet par programmation à une instance de serveur de rapports.  
  
 Reporting Services étant une technologie de création de rapports basée sur le Web, la visionneuse par défaut affiche des rapports qui sont restitués au format HTML.  Si vous ne souhaitez pas utiliser le format HTML comme format de présentation de rapport par défaut, vous devez écrire à une visionneuse de rapports personnalisée pour votre application.  
  
### Création de rapports dans Visual Studio pour Reporting Services  
 Pour générer des rapports qui s'exécutent sur un serveur de rapports, vous devez créer des fichiers de définition de rapport \(.rdl\) dans Visual Studio à l'aide de Business Intelligence Development Studio, qui est inclus avec SQL Server 2005.  
  
> [!NOTE]
>  SQL Server 2005 doit être installé pour que vous puissiez utiliser SQL Server Reporting Services et Business Intelligence Development Studio.  
  
 Business Intelligence Development Studio ajoute des modèles de projet qui sont spécifiques aux composants SQL Server.  Pour créer des rapports, vous avez le choix entre les modèles **Projet Report Server** ou **Assistant Projet Report Server**.  Vous pouvez spécifier des requêtes et des connexions à la source de données pour divers types de source de données, tels que SQL Server, Oracle, Analysis Services, XML et SQL Server Integration Services.  Les onglets **Données**, **Disposition** et **Aperçu** vous permettent de définir des données, de créer une disposition de rapport et d'afficher l'aperçu d'un rapport dans le même espace de travail.  
  
 Les définitions de rapports que vous générez pour le contrôle ou le serveur de rapports peuvent être réutilisées dans l'une ou l'autre de ces technologies.  
  
||  
|-|  
|Pour créer un rapport qui s'exécute sur un serveur de rapports|  
|1.  Dans le menu **Fichier**, choisissez **Nouveau**.<br />     La boîte de dialogue **Nouveau projet** s'affiche.<br />2.  Dans le volet **Types de projet**, cliquez sur **Projets Business Intelligence**.<br />3.  Dans le volet Modèles, sélectionnez **Projet Report Server** ou **Assistant Projet Report Server**.|  
  
## Utilisation conjointe de ReportViewer et de SQL Server Reporting Services  
 Les contrôles ReportViewer et SQL Server 2005 Reporting Services peuvent être utilisés conjointement dans la même application.  
  
-   Le contrôle ReportViewer fournit une visionneuse qui est utilisée pour afficher des rapports dans votre application.  
  
-   Reporting Services fournit les rapports et exécute tout le traitement sur un serveur distant.  
  
 Le contrôle ReportViewer peut être configuré pour afficher des rapports qui sont stockés et traités sur un serveur de rapports Reporting Services distant.  Ce type de configuration est appelé *mode de traitement à distance*.  En mode de traitement à distance, le contrôle demande un rapport qui est stocké sur un serveur de rapports distant.  Le serveur de rapports exécute le traitement de tous les rapports, le traitement des données et le rendu des rapports.  Un rapport fini et rendu est retourné au contrôle et affiché dans la zone d'affichage.  
  
 Les rapports qui s'exécutent sur un serveur de rapports prennent en charge des formats d'exportation supplémentaires, ont une implémentation du paramétrage des rapports différente, utilisent les types de source de données pris en charge par le serveur de rapports et sont accessibles via le modèle d'autorisation par rôle sur le serveur de rapports.  
  
 Pour utiliser le mode de traitement à distance, spécifiez l'URL et le chemin d'accès à un rapport serveur lors de la configuration du contrôle ReportViewer.