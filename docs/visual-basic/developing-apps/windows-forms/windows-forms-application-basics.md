---
title: "Windows Forms bases d’Application (Visual Basic) | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Windows applications
- Windows Forms, Visual Basic
ms.assetid: 0b919d30-7fd6-42db-85c8-543d15312441
caps.latest.revision: 20
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 8275d3c06ebd89254a07127b4850d32ef0580830
ms.lasthandoff: 03/13/2017

---
# <a name="windows-forms-application-basics-visual-basic"></a>Concepts de base de l’application Windows Forms (Visual Basic)
Une partie importante de [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] est la possibilité de créer des applications Windows Forms qui s’exécutent localement sur les ordinateurs des utilisateurs. Vous pouvez utiliser Visual Studio pour créer l’interface utilisateur et d’applications à l’aide de Windows Forms. Une application Windows Forms repose sur les classes de le <xref:System.Windows.Forms>espace de noms.</xref:System.Windows.Forms>  
  
## <a name="designing-windows-forms-applications"></a>Conception de Windows Forms Applications  
 Vous pouvez créer des Windows Forms et les applications de service Windows avec [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]. Pour plus d’informations, consultez les rubriques suivantes :  
  
-   [Prise en main de Windows Forms](https://msdn.microsoft.com/library/ms229601.aspx). Fournit des informations sur la façon de créer et programmer des Windows Forms.  
   
-   [Contrôles Windows Forms](https://msdn.microsoft.com/library/ettb6e2a.aspx). Collection de rubriques détaillant l’utilisation de contrôles Windows Forms.  
  
-   [Applications de Service Windows](https://msdn.microsoft.com/library/y817hyb6.aspx). Répertorie les rubriques qui expliquent comment créer des services Windows.  
  
## <a name="building-rich-interactive-user-interfaces"></a>Création d'interfaces utilisateur interactives et enrichies  
 Windows Forms est le composant client intelligent de la [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)], un ensemble de bibliothèques gérées qui activent des tâches d’application courantes telles que lire et écrire dans le système de fichiers. À l’aide d’un environnement de développement comme [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)], vous pouvez créer des applications Windows Forms qui affichent des informations, demandent des entrées d’utilisateurs et communiqueront avec les ordinateurs distants sur un réseau.  
  
 Dans les Windows Forms, un formulaire est une surface visuelle sur laquelle vous affichez des informations à l’utilisateur. Généralement, vous générez les applications Windows Forms en plaçant contrôles sur les formulaires et en développant des réponses aux actions de l’utilisateur, telles que les clics de souris ou les pressions de touches. A *contrôle* est un élément d’interface utilisateur utilisateur discret qui affiche des données ou accepte une entrée de données.  
  
### <a name="events"></a>Événements  
 Quand un utilisateur modifie un formulaire ou l’un de ses contrôles, il génère un événement. Votre application réagit à ces événements en exécutant du code et traite les événements quand ils se produisent. Pour plus d’informations, consultez [création de gestionnaires d’événements dans les Windows Forms](https://msdn.microsoft.com/library/dacysss4.aspx).  
  
### <a name="controls"></a>Contrôles  
 Windows Forms contient divers contrôles que vous pouvez placer sur les formulaires : contrôles qui affichent des zones de texte, boutons, zones déroulantes, cases d’option et même des pages Web. Pour obtenir la liste de tous les contrôles que vous pouvez utiliser sur un formulaire, consultez la page [contrôles à utiliser dans les Windows Forms](https://msdn.microsoft.com/library/3xdhey7w.aspx). Si un contrôle existant ne répond pas à vos besoins, Windows Forms prend également en charge la création de vos propres contrôles personnalisés à l’aide de la <xref:System.Windows.Forms.UserControl>classe.</xref:System.Windows.Forms.UserControl>  
  
 Windows Forms offre des contrôles d’interface utilisateur enrichis qui émulent les fonctionnalités des applications haut de gamme telles que Microsoft Office. À l’aide de la <xref:System.Windows.Forms.ToolStrip>et <xref:System.Windows.Forms.MenuStrip>(contrôle), vous pouvez créer barres d’outils et des menus qui contiennent du texte et des images, affichent des sous-menus et hébergent d’autres contrôles tels que les zones de texte et les zones de liste déroulante.</xref:System.Windows.Forms.MenuStrip> </xref:System.Windows.Forms.ToolStrip>  
  
 Avec le [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] le Concepteur de formulaires de glisser-déplacer, vous pouvez créer facilement des applications Windows Forms : sélectionnez les contrôles avec votre curseur et placez-les où vous voulez sur le formulaire. Le concepteur fournit des outils tels que les lignes du quadrillage et des « lignes d’alignement » pour simplifier l’alignement des contrôles. Et si vous utilisez [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] ou que vous compiliez sur la ligne de commande, vous pouvez utiliser le <xref:System.Windows.Forms.FlowLayoutPanel>, <xref:System.Windows.Forms.TableLayoutPanel>et <xref:System.Windows.Forms.SplitContainer>dispositions avec un minimum de temps et d’efforts de formulaire des contrôles pour créer des avancées.</xref:System.Windows.Forms.SplitContainer> </xref:System.Windows.Forms.TableLayoutPanel> </xref:System.Windows.Forms.FlowLayoutPanel>  
  
### <a name="custom-ui-elements"></a>Éléments d’interface utilisateur personnalisée  
 Enfin, si vous devez créer vos propres éléments d’interface personnalisés, le <xref:System.Drawing>espace de noms contient toutes les classes nécessaires pour rendre des lignes, des cercles et autres formes directement sur un formulaire.</xref:System.Drawing>  
  
 Pour obtenir des informations détaillées sur l’utilisation de ces fonctionnalités, consultez les rubriques suivantes.  
  
|Pour|Voir|  
|--------|---------|  
|Créez une application Windows Forms avec[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]|[Procédure pas à pas : Création un Windows Form Simple](http://msdn.microsoft.com/en-us/2d9daec0-0543-41d0-acb1-964f685bddbb)|  
|Utiliser des contrôles sur les formulaires|[Comment : ajouter des contrôles aux Windows Forms](https://msdn.microsoft.com/library/0h5y8567.aspx)|   
|Créer des graphismes avec<xref:System.Drawing></xref:System.Drawing>|[Mise en route de la programmation graphique](https://msdn.microsoft.com/library/da0f23z7.aspx)|  
|Créer des contrôles personnalisés|[Comment : hériter de la classe UserControl](https://msdn.microsoft.com/library/00ctb4z0.aspx)|  
  
## <a name="displaying-and-manipulating-data"></a>Affichage et manipulation de données  
 De nombreuses applications doivent afficher des données provenant d’une base de données, d’un fichier XML, d’un service web XML ou autre source de données. Windows Forms fournit un contrôle flexible nommé le <xref:System.Windows.Forms.DataGridView>contrôle pour rendre ces données tabulaires dans un format de ligne et de colonne classique, afin que chaque élément de données occupe sa propre cellule.</xref:System.Windows.Forms.DataGridView> À l’aide de <xref:System.Windows.Forms.DataGridView>vous pouvez personnaliser l’apparence des cellules individuelles, verrouiller des lignes et colonnes en place arbitraires et afficher des contrôles complexes dans les cellules, entre autres fonctionnalités.</xref:System.Windows.Forms.DataGridView>  
  
 La connexion à des sources de données sur un réseau est une tâche simple avec les clients intelligents Windows Forms. Le <xref:System.Windows.Forms.BindingSource>composant, nouveau avec Windows Forms dans [!INCLUDE[vsprvslong](../../../csharp/misc/includes/vsprvslong_md.md)] et [!INCLUDE[dnprdnlong](../../../csharp/programming-guide/events/includes/dnprdnlong_md.md)], représente une connexion à une source de données et expose des méthodes pour lier des données aux contrôles, naviguer vers les enregistrements précédents et suivants, modifier les enregistrements et enregistrer les modifications dans la source d’origine.</xref:System.Windows.Forms.BindingSource> Le <xref:System.Windows.Forms.BindingNavigator>contrôle fournit une interface simple sur le <xref:System.Windows.Forms.BindingSource>composant aux utilisateurs de naviguer entre les enregistrements.</xref:System.Windows.Forms.BindingSource> </xref:System.Windows.Forms.BindingNavigator>  
  
### <a name="data-bound-controls"></a>Contrôles liés aux données  
 Vous pouvez créer des contrôles liés aux données à l’aide de la fenêtre Sources de données, qui affiche des sources de données telles que les bases de données, des services Web et des objets dans votre projet. Pour créer des contrôles liés aux données, vous pouvez faire glisser des éléments depuis cette fenêtre vers des formulaires dans votre projet. Vous pouvez également lier des contrôles existants à des données en faisant glisser des objets depuis la fenêtre Sources de données vers des contrôles existants.  
  
### <a name="settings"></a>Paramètres  
 Un autre type de liaison de données que vous pouvez gérer dans les Windows Forms est paramètres. La plupart des applications smart client doivent conserver des informations sur leur état d’exécution, telles que la dernière taille connue des formulaires et conserver les données de préférence de l’utilisateur, telles que les emplacements par défaut des fichiers enregistrés. La fonctionnalité paramètres de l’application répond à ces exigences en fournissant un moyen facile de stocker les deux types de paramètres sur l’ordinateur client. Une fois définis à l’aide d’une [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] ou un éditeur de code, ces paramètres sont conservés en tant que XML et lus automatiquement en mémoire au moment de l’exécution.  
  
 Pour obtenir des informations détaillées sur l’utilisation de ces fonctionnalités, consultez les rubriques suivantes.  
  
|Pour|Voir|  
|--------|---------|  
|Utilisez le <xref:System.Windows.Forms.BindingSource>composant</xref:System.Windows.Forms.BindingSource>|[Comment : lier des contrôles Windows Forms au composant BindingSource à l’aide du Concepteur](https://msdn.microsoft.com/library/801dxw2t.aspx)|  
|Travailler avec [!INCLUDE[vstecado](../../../csharp/programming-guide/concepts/linq/includes/vstecado_md.md)] des sources de données|[Comment : trier et filtrer des données ADO.NET avec le composant BindingSource Windows Forms](https://msdn.microsoft.com/library/ya3sah92.aspx)|  
|Utilisez la fenêtre Sources de données|[Procédure pas à pas : affichage de données sur un Windows Form](https://docs.microsoft.com/visualstudio/data-tools/accessing-data-in-visual-studio)|  
  
## <a name="deploying-applications-to-client-computers"></a>Déploiement d'applications sur les ordinateurs clients  
 Une fois que vous avez écrit votre application, vous devez l’envoyer à vos utilisateurs afin qu’ils puissent installer et exécuter sur leurs propres ordinateurs clients. À l’aide de la [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)] technologie, vous pouvez déployer vos applications depuis [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] en seulement quelques clics et fournir aux utilisateurs une URL pointant vers votre application sur le Web. [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)]gère tous les éléments et dépendances dans votre application et vérifie que l’application est correctement installée sur l’ordinateur client.  
  
 Vous pouvez configurer les applications [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)] pour qu'elles s'exécutent uniquement quand l'utilisateur est connecté au réseau ou pour qu'elles s'exécutent en ligne et hors connexion. Lorsque vous spécifiez qu’une application doit prendre en charge une opération hors connexion, [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)] ajoute un lien à votre application de l’utilisateur **Démarrer** menu, afin que l’utilisateur puisse l’ouvrir sans utiliser l’URL.  
  
 Quand vous mettez à jour votre application, vous publiez un nouveau manifeste de déploiement et une nouvelle copie de votre application sur votre serveur web. [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)]détecte les mises à jour disponibles et met à niveau l’installation de l’utilisateur ; aucune programmation personnalisée n’est requise pour mettre à jour les anciens assemblys.  
  
 Pour une introduction complète à [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)], consultez [sécurité et déploiement ClickOnce](https://docs.microsoft.com/visualstudio/deployment/clickonce-security-and-deployment). Pour obtenir des informations détaillées sur l’utilisation de ces fonctionnalités, consultez les rubriques suivantes :  
  
|Pour|Voir|  
|--------|---------|  
|Déployer une application avec[!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)]|[Guide pratique pour publier une application ClickOnce à l’aide de l’Assistant Publication](https://docs.microsoft.com/visualstudio/deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard)<br /><br /> [Procédure pas à pas : déploiement manuel d’une application ClickOnce](https://docs.microsoft.com/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)|  
|Mise à jour un [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)] déploiement|[Guide pratique pour gérer les mises à jour pour une application ClickOnce](https://docs.microsoft.com/visualstudio/deployment/how-to-manage-updates-for-a-clickonce-application)|  
|Gérer la sécurité avec[!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)]|[Guide pratique pour activer les paramètres de sécurité ClickOnce](https://docs.microsoft.com/visualstudio/deployment/how-to-enable-clickonce-security-settings)|  
  
## <a name="other-controls-and-features"></a>Autres contrôles et fonctionnalités  
 Il existe de nombreuses autres fonctionnalités dans Windows Forms qui simplifient et accélèrent l'implémentation des tâches courantes, par exemple la prise en charge de la création de boîtes de dialogue, de l'impression, de l'ajout d'aide et de documentation et de la localisation de votre application en plusieurs langues. En outre, Windows Forms repose sur le système de sécurité fiable de la [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)], ce qui vous permet de distribuer des applications plus sécurisées à vos clients.  
  
 Pour obtenir des informations détaillées sur l’utilisation de ces fonctionnalités, consultez les rubriques suivantes :  
  
|Pour|Voir|  
|--------|---------|  
|Imprimer le contenu d’un formulaire|[Comment : imprimer des graphiques dans les Windows Forms](https://msdn.microsoft.com/library/741a0ktc.aspx)<br /><br /> [Comment : imprimer un fichier texte de plusieurs pages dans les Windows Forms](https://msdn.microsoft.com/library/cwbe712d.aspx)|   
|En savoir plus sur la sécurité Windows Forms|[Sécurité dans la vue d’ensemble des Windows Forms](https://msdn.microsoft.com/library/90k49ccb.aspx)|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase></xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>   
 [Vue d’ensemble des Windows Forms](https://msdn.microsoft.com/library/8bxxy49h.aspx)   
 [My.Forms (objet)](../../../visual-basic/language-reference/objects/my-forms-object.md)
