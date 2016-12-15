---
title: "Proc&#233;dure pas &#224; pas&#160;: affichage de donn&#233;es dans un contr&#244;le DataRepeater (Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "DataRepeater, procédure pas à pas"
ms.assetid: 65dcdb95-6c3e-47cc-987d-190000f71653
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Proc&#233;dure pas &#224; pas&#160;: affichage de donn&#233;es dans un contr&#244;le DataRepeater (Visual Studio)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Cette procédure pas à pas propose un scénario complet de base permettant d’afficher des données liées dans un contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.  
  
## Composants requis  
 Cette procédure pas à pas requiert l'exemple de base de données Northwind.  
  
 Si cette base de données n’est pas disponible sur votre ordinateur de développement, vous pouvez la télécharger à partir du [Centre de téléchargement Microsoft](http://go.microsoft.com/fwlink/?LinkID=98088). Pour obtenir des instructions, consultez [Téléchargement d'exemples de bases de données](../Topic/Downloading%20Sample%20Databases.md).  
  
## Vue d'ensemble  
 La première partie de cette procédure pas à pas se compose de quatre tâches principales :  
  
-   Création d’une solution.  
  
-   Ajout d’un contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.  
  
-   Ajout d’une source de données.  
  
-   Ajout de contrôles liés aux données.  
  
 [!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
## Création d’une solution DataRepeater.  
 Dans la première étape, vous allez créer un projet et une solution.  
  
#### Pour créer une solution DataRepeater  
  
1.  Dans le menu **Fichier** de Visual Studio, cliquez sur **Nouveau projet**.  
  
2.  Dans le volet **Types de projets** dans la boîte de dialogue **Nouveau projet**, développez **Visual Basic**, puis cliquez sur **Windows**.  
  
3.  Dans le volet **Modèles**, cliquez sur **Application Windows Forms**.  
  
4.  Dans la zone **Nom**, tapez `DataRepeaterApp`.  
  
5.  Cliquez sur **OK**.  
  
     Le Concepteur Windows Forms s'ouvre.  
  
6.  Sélectionnez le formulaire dans le Concepteur Windows Forms. Dans la fenêtre **Propriétés**, affectez à la propriété **Size** la valeur `800, 700`.  
  
## Ajout d’un contrôle DataRepeater  
 Dans cette étape, vous allez ajouter un contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> au formulaire.  
  
#### Pour ajouter un contrôle DataRepeater  
  
1.  Dans le menu **Affichage**, cliquez sur **Boîte à outils**.  
  
     La **Boîte à outils** s'ouvre.  
  
2.  Sélectionnez l’onglet **Visual Basic PowerPack**.  
  
3.  Faites glisser un contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> sur **Form1**.  
  
4.  Dans la fenêtre Propriétés, affectez à la propriété **Location** la valeur `0, 25`.  
  
5.  Affectez à la propriété **Size** la valeur `460, 600`.  
  
## Ajout d’une source de données  
 Dans cette étape, vous allez ajouter une source de données pour le contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.  
  
#### Pour ajouter une source de données  
  
1.  Dans le menu **Données**, cliquez sur **Afficher les sources de données**.  
  
2.  Dans la fenêtre **Sources de données**, cliquez sur **Ajouter une nouvelle source de données**.  
  
3.  Sélectionnez **Base de données** dans la page **Choisir un type de source de données**, puis cliquez sur **Suivant**.  
  
4.  Sur la page **Choisir votre connexion de données**, effectuez l'une des opérations suivantes :  
  
    -   Si une connexion de données à l'exemple de base de données Northwind est disponible dans la liste déroulante, sélectionnez\-la.  
  
         ou  
  
    -   Cliquez sur le bouton **Nouvelle connexion** pour configurer une nouvelle connexion de données. Pour plus d'informations, consultez [How to: Create Connections to SQL Server Databases](http://msdn.microsoft.com/fr-fr/360c340d-e5a6-4a7e-a569-e95d500be43d).  
  
5.  Si la base de données requiert un mot de passe, sélectionnez l'option permettant d'inclure les données sensibles, puis cliquez sur **Suivant**.  
  
    > [!NOTE]
    >  Si une boîte de dialogue s’affiche, cliquez sur **Oui** pour enregistrer le fichier dans votre projet.  
  
6.  Cliquez sur **Suivant** dans la page **Enregistrer la chaîne de connexion dans le fichier de configuration de l’application**.  
  
7.  Développez le nœud **Tables** dans la page **Choisir vos objets de base de données**.  
  
8.  Cochez les cases correspondant aux tables **Customers** et **Orders**, puis cliquez sur **Terminer**.  
  
     **NorthwindDataSet** est ajouté à votre projet et les tables **Customers** et **Orders** apparaissent dans la fenêtre **Sources de données**.  
  
## Ajout de contrôles liés aux données  
 Dans cette étape, vous allez ajouter des contrôles liés aux données à <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.  
  
#### Pour ajouter des contrôles liés aux données  
  
1.  Dans la fenêtre **Sources de données**, sélectionnez le nœud de niveau supérieur pour la table **Customers**.  
  
2.  Choisissez le type de déplacement **Détails** pour la table en cliquant sur **Détails** dans la liste déroulante du nœud de la table.  
  
3.  Sélectionnez le nœud de la table **Customers** et faites\-le glisser vers la région du modèle d’élément \(région du haut\) du contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.  
  
     Un contrôle <xref:System.Windows.Forms.BindingNavigator> est ajouté au formulaire et les composants **NorthwindDataSet**, **CustomersBindingSource**, **CustomersTableAdapter**, **TableAdapterManager** et **CustomersBindingNavigator** sont ajoutés à la barre d’état des composants.  
  
4.  Sélectionnez tous les champs et les étiquettes associées et placez\-les à proximité de la bordure gauche de la région du modèle d’élément.  
  
5.  Sélectionnez les cinq derniers champs \(**Region**, **Postal Code**, **Country**, **Phone** et **Fax**\) et les étiquettes associées ,puis déplacez\-les en haut à droite des six premiers champs.  
  
6.  Sélectionnez le modèle d’élément \(région supérieure du contrôle\).  
  
7.  Dans la fenêtre Propriétés, affectez à la propriété **Size** la valeur `427, 170`.  
  
 À ce stade, vous disposez d’une application opérationnelle qui affiche une liste récurrente de clients. Vous pouvez appuyer sur F5 pour exécuter l’application, modifier les données et ajouter ou supprimer des enregistrements client.  
  
 Dans les étapes facultatives suivantes, vous allez apprendre à personnaliser le contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.  
  
## Étapes suivantes \(facultatif\)  
 Cette partie de la procédure pas à pas comporte quatre tâches facultatives :  
  
-   Modification de l’apparence du contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.  
  
-   Ajout d’une interdiction d’ajout ou de suppression des enregistrements.  
  
-   Ajout d’une fonction de recherche au contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.  
  
-   Ajout d’une table principale et détaillée au contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.  
  
## Modification de l’apparence du contrôle DataRepeater  
 Dans cette étape facultative, vous allez modifier la propriété `BackColor` du contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> au moment du design. Vous allez aussi ajouter du code pour afficher les lignes dans des couleurs qui alternent et modifier la propriété `ForeColor` d’une étiquette de façon conditionnelle.  
  
#### Pour modifier l’apparence du contrôle  
  
1.  Dans le Concepteur Windows Forms, sélectionnez la région principale \(inférieure\) du contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.  
  
2.  Dans la fenêtre Propriétés, définissez la propriété `BackColor` en choisissant le blanc.  
  
3.  Double\-cliquez sur le bouton <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> pour ouvrir l’éditeur de code.  
  
4.  Dans l’éditeur de code, dans la liste déroulante d’événements, cliquez sur **DrawItem**.  
  
5.  Dans le gestionnaire d’événements <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>, ajoutez le code suivant pour alterner les couleurs via `BackColor`.  
  
     [!code-cs[VbPowerPacksDataRepeaterWalkthrough#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_1.vb)]  
  
6.  Dans le gestionnaire d’événements <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>, ajoutez le code suivant pour modifier la propriété `ForeColor` d’une étiquette en fonction d’une condition :  
  
     [!code-cs[VbPowerPacksDataRepeaterWalkthrough#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_2.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_2.vb)]  
  
7.  Appuyez sur F5 pour exécuter l’application et visualiser les personnalisations.  
  
## Interdiction d’ajout ou de suppression des enregistrements  
 Dans cette étape facultative, vous allez ajouter du code pour empêcher les utilisateurs d’ajouter ou de supprimer des enregistrements dans le contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.  
  
#### Pour empêcher les utilisateurs d’ajouter et de supprimer des enregistrements  
  
1.  Dans le Concepteur Windows Forms, double\-cliquez sur le formulaire pour ouvrir l’éditeur de code.  
  
2.  Ajoutez le code suivant à l’événement `Form_Load`.  
  
     [!code-cs[VbPowerPacksDataRepeaterWalkthrough#3](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_3.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#3](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_3.vb)]  
  
3.  Dans la liste déroulante Nom de la classe, cliquez sur **BindingNavigatorDeleteItem**. Dans la liste déroulante Nom de la méthode, cliquez sur **EnabledChanged**.  
  
4.  Ajoutez le code suivant au gestionnaire d'événements `BindingNavigatorDeleteItem_EnabledChanged` :  
  
     [!code-cs[VbPowerPacksDataRepeaterWalkthrough#4](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_4.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#4](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_4.vb)]  
  
    > [!NOTE]
    >  Cette étape est nécessaire car <xref:System.Windows.Forms.BindingSource> active le bouton **DeleteItem** chaque fois que l’enregistrement actif est modifié.  
  
5.  Appuyez sur F5 pour exécuter l'application. Notez que le bouton **DeleteItem** est désactivé et que vous ne pouvez pas supprimer des éléments en appuyant sur la touche SUPPR.  
  
## Ajout d’une fonction de recherche au contrôle DataRepeater  
 Dans cette étape facultative, vous allez implémenter une fonction de recherche de valeurs dans le contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>. Si la chaîne recherchée est trouvée, le contrôle sélectionne l’élément qui contient la valeur et affiche cet élément.  
  
#### Pour ajouter la fonction de recherche  
  
1.  Faites glisser un contrôle <xref:System.Windows.Forms.TextBox> de la **Boîte à outils** vers le formulaire qui contient le contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.  
  
     Placez\-le sous le contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.  
  
2.  Dans la fenêtre Propriétés, attribuez à la propriété **Name** la valeur **SearchTextBox**.  
  
3.  Faites glisser un contrôle <xref:System.Windows.Forms.Button> de la **Boîte à outils** vers le formulaire qui contient le contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>. Placez\-le sous le contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.  
  
4.  Dans la fenêtre Propriétés, attribuez à la propriété **Name** la valeur **SearchButton**. Affectez à la propriété **Text** la valeur **Search**.  
  
5.  Double\-cliquez sur le contrôle <xref:System.Windows.Forms.Button> pour ouvrir l’éditeur de code et ajoutez le code suivant au gestionnaire d’événements `SearchButton_Click`.  
  
     [!code-cs[VbPowerPacksDataRepeaterWalkthrough#5](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_5.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#5](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_5.vb)]  
  
6.  Appuyez sur F5 pour exécuter l'application. Tapez un ID client dans **SearchTextBox** et cliquez sur le bouton **Search**.  
  
## Ajout d’une table principale et détaillée au contrôle DataRepeater  
 Dans cette étape facultative, vous allez ajouter un deuxième contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> pour afficher les commandes associées à chaque client.  
  
#### Pour ajouter une table principale et détaillée  
  
1.  Faites glisser un deuxième contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> de l’onglet **Visual Basic PowerPacks** de la **Boîte à outils** vers le formulaire.  
  
2.  Dans la fenêtre Propriétés, affectez à la propriété **Location** la valeur `465, 25`.  
  
3.  Affectez à la propriété **Size** la valeur `315, 600`.  
  
4.  Dans la fenêtre **Sources de données**, développez le nœud de la table **Customers** et sélectionnez le nœud détaillé de la table **Orders**.  
  
5.  Modifiez le type de déplacement de cette table **Orders** en cliquant sur **Détails** dans la liste déroulante du nœud de la table.  
  
6.  Faites glisser le nœud de cette table **Orders** vers la région du modèle d’élément \(région supérieure\) du deuxième contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.  
  
     Un composant **OrdersBindingSource** et un composant **OrdersTableAdapter** sont ajoutés à la barre d’état des composants.  
  
7.  Appuyez sur F5 pour exécuter l'application. Quand vous sélectionnez un client dans le premier contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>, les commandes de ce client s’affichent dans le deuxième contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.  
  
## Voir aussi  
 [Introduction to the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)   
 [How to: Display Bound Data in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)   
 [How to: Display Unbound Controls in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)   
 [How to: Change the Layout of a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md)   
 [How to: Display Item Headers in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md)   
 [How to: Search Data in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-search-data-in-a-datarepeater-control-visual-studio.md)   
 [How to: Create a Master\/Detail Form by Using Two DataRepeater Controls](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)   
 [How to: Change the Appearance of a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)   
 [How to: Disable Adding and Deleting DataRepeater Items](../../../visual-basic/developing-apps/windows-forms/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio.md)   
 [Troubleshooting the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)