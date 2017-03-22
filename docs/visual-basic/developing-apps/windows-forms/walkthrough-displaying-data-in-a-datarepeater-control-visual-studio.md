---
title: "Procédure pas à pas : Affichage des données dans un contrôle DataRepeater (Visual Studio) | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- DataRepeater, walkthrough
ms.assetid: 65dcdb95-6c3e-47cc-987d-190000f71653
caps.latest.revision: 12
author: stevehoag
ms.author: shoag
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 09f15c94c3d5a3387935c8d3f4758c0ecfd7cfcd
ms.lasthandoff: 03/13/2017

---
# <a name="walkthrough-displaying-data-in-a-datarepeater-control-visual-studio"></a>Procédure pas à pas : affichage de données dans un contrôle DataRepeater (Visual Studio)
Cette procédure pas à pas fournit un scénario de démarrage à la fin de base pour afficher les données liées dans un <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
## <a name="prerequisite"></a>Prérequis  
 Cette procédure pas à pas requiert l'exemple de base de données Northwind.  
  
 Si cette base de données n’est pas disponible sur votre ordinateur de développement, vous pouvez la télécharger à partir du [Centre de téléchargement Microsoft](http://go.microsoft.com/fwlink/?LinkID=98088). Pour obtenir des instructions, consultez la page [téléchargement d’exemples de bases de données](https://msdn.microsoft.com/library/bb399411).  
  
## <a name="overview"></a>Vue d'ensemble  
 La première partie de cette procédure pas à pas se compose de quatre tâches principales :  
  
-   Création d’une solution.  
  
-   Ajout d’un <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
-   Ajout d’une source de données.  
  
-   Ajout de contrôles liés aux données.  
  
[!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
## <a name="creating-a-datarepeater-solution"></a>Création d’une solution DataRepeater.  
 Dans la première étape, vous allez créer un projet et une solution.  
  
#### <a name="to-create-a-datarepeater-solution"></a>Pour créer une solution DataRepeater  
  
1.  Dans le menu **Fichier** de Visual Studio, cliquez sur **Nouveau projet**.  
  
2.  Dans le volet **Types de projets** dans la boîte de dialogue **Nouveau projet** , développez **Visual Basic**, puis cliquez sur **Windows**.  
  
3.  Dans le volet **Modèles** , cliquez sur **Application Windows Forms**.  
  
4.  Dans la zone **Nom** , tapez `DataRepeaterApp`.  
  
5.  Cliquez sur **OK**.  
  
     Le Concepteur Windows Forms s'ouvre.  
  
6.  Sélectionnez le formulaire dans le Concepteur Windows Forms. Dans la fenêtre **Propriétés** , affectez à la propriété **Size** la valeur `800, 700`.  
  
## <a name="adding-a-datarepeater-control"></a>Ajout d’un contrôle DataRepeater  
 Dans cette étape, vous allez ajouter un <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôle au formulaire.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
#### <a name="to-add-a-datarepeater-control"></a>Pour ajouter un contrôle DataRepeater  
  
1.  Dans le menu **Affichage** , cliquez sur **Boîte à outils**.  
  
     La **Boîte à outils** s'ouvre.  
  
2.  Sélectionnez l’onglet **Visual Basic PowerPack** .  
  
3.  Faites glisser un <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôler sur **Form1**.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
4.  Dans la fenêtre Propriétés, affectez à la propriété **Location** la valeur `0, 25`.  
  
5.  Affectez à la propriété **Size** la valeur `460, 600`.  
  
## <a name="adding-a-data-source"></a>Ajout d’une source de données  
 Dans cette étape, vous ajoutez une source de données pour la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
#### <a name="to-add-a-data-source"></a>Pour ajouter une source de données  
  
1.  Dans le menu **Données** , cliquez sur **Afficher les sources de données**.  
  
2.  Dans la fenêtre **Sources de données** , cliquez sur **Ajouter une nouvelle source de données**.  
  
3.  Sélectionnez **Base de données** dans la page **Choisir un type de source de données** , puis cliquez sur **Suivant**.  
  
4.  Sur la page **Choisir votre connexion de données** , effectuez l'une des opérations suivantes :  
  
    -   Si une connexion de données à l'exemple de base de données Northwind est disponible dans la liste déroulante, sélectionnez-la.  
  
         ou  
  
    -   Cliquez sur le bouton **Nouvelle connexion** pour configurer une nouvelle connexion de données. Pour plus d’informations, consultez [Comment : créer des connexions aux bases de données SQL Server](http://msdn.microsoft.com/en-us/360c340d-e5a6-4a7e-a569-e95d500be43d).  
  
5.  Si la base de données requiert un mot de passe, sélectionnez l'option permettant d'inclure les données sensibles, puis cliquez sur **Suivant**.  
  
    > [!NOTE]
    >  Si une boîte de dialogue s’affiche, cliquez sur **Oui** pour enregistrer le fichier dans votre projet.  
  
6.  Cliquez sur **Suivant** dans la page **Enregistrer la chaîne de connexion dans le fichier de configuration de l’application** .  
  
7.  Développez le nœud **Tables** dans la page **Choisir vos objets de base de données** .  
  
8.  Cochez les cases correspondant aux tables **Customers** et **Orders** , puis cliquez sur **Terminer**.  
  
     **NorthwindDataSet** est ajouté à votre projet et les tables **Customers** et **Orders** apparaissent dans la fenêtre **Sources de données** .  
  
## <a name="adding-data-bound-controls"></a>Ajout de contrôles liés aux données  
 Dans cette étape, vous allez ajouter des contrôles liés aux données le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
#### <a name="to-add-data-bound-controls"></a>Pour ajouter des contrôles liés aux données  
  
1.  Dans la fenêtre **Sources de données** , sélectionnez le nœud de niveau supérieur pour la table **Customers** .  
  
2.  Choisissez le type de déplacement **Détails** pour la table en cliquant sur **Détails** dans la liste déroulante du nœud de la table.  
  
3.  Sélectionnez le **clients** table nœud et faites-le glisser sur la région de modèle d’élément (région supérieure) de la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
     Un <xref:System.Windows.Forms.BindingNavigator>contrôle est ajouté au formulaire et la **NorthwindDataSet**, **CustomersBindingSource**, **CustomersTableAdapter**, **TableAdapterManager**, et **CustomersBindingNavigator** composants sont ajoutés à la barre d’état du composant.</xref:System.Windows.Forms.BindingNavigator>  
  
4.  Sélectionnez tous les champs et les étiquettes associées et placez-les à proximité de la bordure gauche de la région du modèle d’élément.  
  
5.  Sélectionnez les cinq derniers champs (**Region**, **Postal Code**, **Country**, **Phone**et **Fax**) et les étiquettes associées ,puis déplacez-les en haut à droite des six premiers champs.  
  
6.  Sélectionnez le modèle d’élément (région supérieure du contrôle).  
  
7.  Dans la fenêtre Propriétés, affectez à la propriété **Size** la valeur `427, 170`.  
  
 À ce stade, vous disposez d’une application opérationnelle qui affiche une liste récurrente de clients. Vous pouvez appuyer sur F5 pour exécuter l’application, modifier les données et ajouter ou supprimer des enregistrements client.  
  
 Lors des étapes facultatives suivantes, vous allez apprendre à personnaliser le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
## <a name="next-steps-optional"></a>Étapes suivantes (facultatif)  
 Cette partie de la procédure pas à pas comporte quatre tâches facultatives :  
  
-   Modification de l’apparence de la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
-   Ajout d’une interdiction d’ajout ou de suppression des enregistrements.  
  
-   Ajout de la fonction de recherche pour la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
-   Ajout d’une table maître et détail vers le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
## <a name="changing-the-appearance-of-the-datarepeater-control"></a>Modification de l’apparence du contrôle DataRepeater  
 Cette étape facultative, vous modifiez le `BackColor` de la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôle au moment du design.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Vous allez aussi ajouter du code pour afficher les lignes dans des couleurs qui alternent et modifier la propriété `ForeColor` d’une étiquette de façon conditionnelle.  
  
#### <a name="to-change-the-appearance-of-the-control"></a>Pour modifier l’apparence du contrôle  
  
1.  Dans le Concepteur Windows Forms, sélectionnez la région principale (inférieure) de la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
2.  Dans la fenêtre Propriétés, définissez la propriété `BackColor` en choisissant le blanc.  
  
3.  Double-cliquez sur le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>pour ouvrir l’éditeur de Code.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
4.  Dans l’éditeur de code, dans la liste déroulante d’événements, cliquez sur **DrawItem**.  
  
5.  Dans la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>Gestionnaire d’événements, ajoutez le code suivant pour alterner la `BackColor`:</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>  
  
     [!code-cs[N °&1; de VbPowerPacksDataRepeaterWalkthrough](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_1.cs) ] 
     [!code-vb [VbPowerPacksDataRepeaterWalkthrough n °&1;](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_1.vb)]  
  
6.  Dans la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>Gestionnaire d’événements, ajoutez le code suivant pour modifier la `ForeColor` d’une étiquette en fonction d’une condition :</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>  
  
     [!code-cs[VbPowerPacksDataRepeaterWalkthrough n °&2;](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_2.cs) ] 
     [!code-vb [VbPowerPacksDataRepeaterWalkthrough n °&2;](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_2.vb)]  
  
7.  Appuyez sur F5 pour exécuter l’application et visualiser les personnalisations.  
  
## <a name="preventing-users-from-adding-or-deleting-records"></a>Interdiction d’ajout ou de suppression des enregistrements  
 Cette étape facultative, vous ajoutez le code qui empêche les utilisateurs d’ajouter ou supprimer des enregistrements dans la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
#### <a name="to-prevent-users-from-adding-and-deleting-records"></a>Pour empêcher les utilisateurs d’ajouter et de supprimer des enregistrements  
  
1.  Dans le Concepteur Windows Forms, double-cliquez sur le formulaire pour ouvrir l’éditeur de code.  
  
2.  Ajoutez le code suivant à l’événement `Form_Load` .  
  
     [!code-cs[VbPowerPacksDataRepeaterWalkthrough n °&3;](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_3.cs) ] 
     [!code-vb [VbPowerPacksDataRepeaterWalkthrough n°&3;](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_3.vb)]  
  
3.  Dans la liste déroulante Nom de la classe, cliquez sur **BindingNavigatorDeleteItem**. Dans la liste déroulante Nom de la méthode, cliquez sur **EnabledChanged**.  
  
4.  Ajoutez le code suivant au gestionnaire d'événements `BindingNavigatorDeleteItem_EnabledChanged` :  
  
     [!code-cs[VbPowerPacksDataRepeaterWalkthrough n °&4;](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_4.cs) ] 
     [!code-vb [VbPowerPacksDataRepeaterWalkthrough n °&4;](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_4.vb)]  
  
    > [!NOTE]
    >  Cette étape est nécessaire car le <xref:System.Windows.Forms.BindingSource>activera le **DeleteItem** bouton chaque fois que l’enregistrement actuel est modifié.</xref:System.Windows.Forms.BindingSource>  
  
5.  Appuyez sur F5 pour exécuter l'application. Notez que le bouton **DeleteItem** est désactivé et que vous ne pouvez pas supprimer des éléments en appuyant sur la touche SUPPR.  
  
## <a name="adding-search-capability-to-the-datarepeater-control"></a>Ajout d’une fonction de recherche au contrôle DataRepeater  
 Cette étape facultative, vous implémentez la fonction de recherche d’une valeur dans la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Si la chaîne recherchée est trouvée, le contrôle sélectionne l’élément qui contient la valeur et affiche cet élément.  
  
#### <a name="to-add-search-capability"></a>Pour ajouter la fonction de recherche  
  
1.  Faites glisser un <xref:System.Windows.Forms.TextBox>contrôler à partir de la **boîte à outils** sur le formulaire qui contient le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> </xref:System.Windows.Forms.TextBox>  
  
     Placez-la sous la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
2.  Dans la fenêtre Propriétés, attribuez à la propriété **Name** la valeur **SearchTextBox**.  
  
3.  Faites glisser un <xref:System.Windows.Forms.Button>contrôler à partir de la **boîte à outils** sur le formulaire qui contient le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> </xref:System.Windows.Forms.Button> Placez-la sous la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
4.  Dans la fenêtre Propriétés, attribuez à la propriété **Name** la valeur **SearchButton**. Affectez à la propriété **Text** la valeur **Search**.  
  
5.  Double-cliquez sur le <xref:System.Windows.Forms.Button>contrôler pour ouvrir l’éditeur de Code et ajoutez le code suivant à la `SearchButton_Click` Gestionnaire d’événements.</xref:System.Windows.Forms.Button>  
  
     [!code-cs[VbPowerPacksDataRepeaterWalkthrough&5;](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_5.cs) ] 
     [!code-vb [VbPowerPacksDataRepeaterWalkthrough n °&5;](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_5.vb)]  
  
6.  Appuyez sur F5 pour exécuter l'application. Tapez un ID client dans **SearchTextBox** et cliquez sur le bouton **Search** .  
  
## <a name="adding-a-master-and-detail-table-to-the-datarepeater"></a>Ajout d’une table principale et détaillée au contrôle DataRepeater  
 Cette étape facultative, vous ajoutez un deuxième <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôle pour afficher les commandes associées à chaque client.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
#### <a name="to-add-a-master-and-detail-table"></a>Pour ajouter une table principale et détaillée  
  
1.  Faites glisser un deuxième <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôler à partir de la **Visual Basic PowerPacks** onglet dans le **boîte à outils** sur le formulaire.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
2.  Dans la fenêtre Propriétés, affectez à la propriété **Location** la valeur `465, 25`.  
  
3.  Affectez à la propriété **Size** la valeur `315, 600`.  
  
4.  Dans la fenêtre **Sources de données** , développez le nœud de la table **Customers** et sélectionnez le nœud détaillé de la table **Orders** .  
  
5.  Modifiez le type de déplacement de cette table **Orders** en cliquant sur **Détails** dans la liste déroulante du nœud de la table.  
  
6.  Faites glisser ce **commandes** sur la région de modèle d’élément (région supérieure) du deuxième nœud de la table <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
     Un composant **OrdersBindingSource** et un composant **OrdersTableAdapter** sont ajoutés à la barre d’état des composants.  
  
7.  Appuyez sur F5 pour exécuter l'application. Lorsque vous sélectionnez chacun des clients dans la première <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôler, les commandes de ce client s’affichent dans la seconde <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
## <a name="see-also"></a>Voir aussi  
 [Introduction au contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)   
 [Comment : afficher des données liées dans un contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)   
 [Comment : afficher les contrôles indépendants dans un contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)   
 [Comment : modifier la disposition d’un contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md)   
 [Comment : afficher des en-têtes d’élément dans un contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md)   
 [Comment : rechercher des données dans un contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-search-data-in-a-datarepeater-control-visual-studio.md)   
 [Comment : créer un formulaire maître/détail en utilisant deux contrôles DataRepeater (Visual Studio)](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)   
 [Comment : modifier l’apparence d’un contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)   
 [Comment : désactiver l’ajout et la suppression d’éléments du contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio.md)   
 [Dépannage des problèmes liés au contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
