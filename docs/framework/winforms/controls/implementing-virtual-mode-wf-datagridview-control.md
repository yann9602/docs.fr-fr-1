---
title: "Proc&#233;dure pas &#224; pas&#160;: impl&#233;mentation du mode virtuel dans le contr&#244;le DataGridView Windows Forms | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "données (Windows Forms), gérer de grands groupes de données"
  - "DataGridView (contrôle Windows Forms), grands groupes de données"
  - "DataGridView (contrôle Windows Forms), mode virtuel"
  - "mode virtuel, procédures pas à pas"
  - "procédures pas à pas (Windows Forms), DataGridView (contrôle)"
ms.assetid: 74eb5276-5ab8-4ce0-8005-dae751d85f7c
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Proc&#233;dure pas &#224; pas&#160;: impl&#233;mentation du mode virtuel dans le contr&#244;le DataGridView Windows Forms
Lorsque vous souhaitez afficher de très grandes quantités de données sous forme de tableau dans un contrôle <xref:System.Windows.Forms.DataGridView>, vous pouvez affecter à la propriété <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> la valeur `true` et gérer explicitement l'interaction du contrôle avec son magasin de données.  Cela vous permet de régler avec précision la performance du contrôle dans cette situation.  
  
 Le contrôle <xref:System.Windows.Forms.DataGridView> fournit plusieurs événements que vous pouvez gérer pour interagir avec un magasin de données personnalisé.  Cette procédure pas à pas vous guide à travers le processus d'implémentation de ces gestionnaires d'événements.  L'exemple de code dans cette rubrique utilise une source de données très simple au titre d'illustration.  Dans un cadre de production, vous chargez en général uniquement les lignes que vous devez afficher dans un cache, et gérez les événements <xref:System.Windows.Forms.DataGridView> pour interagir avec le cache et le mettre à jour.  Pour plus d'informations, consultez [Implémentation du mode virtuel avec le chargement de données juste\-à\-temps dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)  
  
 Pour copier le code dans cette rubrique sous forme de liste unique, consultez [Comment : implémenter le mode virtuel dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md).  
  
## Création du formulaire  
  
#### Pour implémenter le mode virtuel  
  
1.  Créez une classe qui dérive de <xref:System.Windows.Forms.Form> et contient un contrôle <xref:System.Windows.Forms.DataGridView>.  
  
     Le code suivant contient une initialisation de base.  Il déclare quelques variables qui seront utilisées dans les étapes ultérieures, fournit une méthode `Main` et fournit une présentation de formulaire simple dans le constructeur de classe.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#001](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#001)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#001](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#001)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#001](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#001)]  
    [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#002](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#002)]
    [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#002](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#002)]
    [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#002](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#002)]  
  
2.  Implémentez un gestionnaire pour l'événement <xref:System.Windows.Forms.Form.Load> de votre formulaire qui initialise le contrôle <xref:System.Windows.Forms.DataGridView> et remplit le magasin de données avec des valeurs d'échantillon.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#110](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#110)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#110](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#110)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#110](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#110)]  
  
3.  Implémentez un gestionnaire pour l'événement <xref:System.Windows.Forms.DataGridView.CellValueNeeded> qui récupère la valeur de cellule demandée dans le magasin de données ou l'objet `Customer` en cours de modification.  
  
     Cet événement se produit chaque fois que le contrôle <xref:System.Windows.Forms.DataGridView> doit peindre une cellule.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#120](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#120)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#120](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#120)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#120](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#120)]  
  
4.  Implémentez un gestionnaire pour l'événement <xref:System.Windows.Forms.DataGridView.CellValuePushed> qui stocke une valeur de cellule modifiée dans l'objet `Customer` qui représente la ligne modifiée.  Cet événement se produit chaque fois que l'utilisateur valide un changement de valeur de la cellule.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#130](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#130)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#130](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#130)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#130](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#130)]  
  
5.  Implémentez un gestionnaire pour l'événement <xref:System.Windows.Forms.DataGridView.NewRowNeeded> qui crée un nouvel objet `Customer` représentant une ligne nouvellement créée.  
  
     Cet événement se produit chaque fois que l'utilisateur entre dans la ligne pour de nouveaux enregistrements.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#140](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#140)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#140](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#140)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#140](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#140)]  
  
6.  Implémentez un gestionnaire pour l'événement <xref:System.Windows.Forms.DataGridView.RowValidated> qui enregistre les lignes nouvelles ou modifiées dans le magasin de données.  
  
     Cet événement se produit chaque fois que l'utilisateur change la ligne actuelle.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#150](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#150)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#150](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#150)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#150](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#150)]  
  
7.  Implémentez un gestionnaire pour l'événement <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> qui indique si l'événement <xref:System.Windows.Forms.DataGridView.CancelRowEdit> se produit lorsque l'utilisateur signale une inversion de ligne en appuyant deux fois sur ÉCHAP en mode édition, ou une fois dans un autre mode.  
  
     Par défaut, <xref:System.Windows.Forms.DataGridView.CancelRowEdit> se produit en cas d'inversion de ligne lorsque chaque cellule de la ligne actuelle a été modifiée, sauf si la propriété <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=fullName> a la valeur `true` dans le gestionnaire d'événements <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>.  Cet événement est utile lorsque la portée de validation est déterminée au moment de l'exécution.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#160](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#160)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#160](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#160)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#160](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#160)]  
  
8.  Implémentez un gestionnaire pour l'événement <xref:System.Windows.Forms.DataGridView.CancelRowEdit> qui ignore les valeurs de l'objet `Customer` représentant la ligne actuelle.  
  
     Cet événement se produit lorsque l'utilisateur signale l'inversion de ligne en appuyant deux fois sur ÉCHAP en mode édition, ou une fois dans un autre mode.  Cet événement ne se produit pas si aucune cellule de la ligne actuelle n'a été modifiée ou si la valeur `false` a été affectée à la propriété <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=fullName> dans un gestionnaire d'événements <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#170](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#170)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#170](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#170)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#170](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#170)]  
  
9. Implémentez un gestionnaire pour l'événement <xref:System.Windows.Forms.DataGridView.UserDeletingRow> qui supprime un objet `Customer` existant dans le magasin de données ou ignore un objet `Customer` non enregistré qui représente une ligne venant d'être créée.  
  
     Cet événement se produit chaque fois que l'utilisateur supprime une ligne en cliquant sur un en\-tête de ligne et en appuyant sur la touche SUPPR.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#180](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#180)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#180](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#180)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#180](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#180)]  
  
10. Implémentez une classe `Customers` simple pour représenter les éléments de données utilisés par cet exemple de code.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#200](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#200)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#200](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#200)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#200](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#200)]  
  
## Test de l'application  
 Vous pouvez à présent tester le formulaire afin de vous assurer qu'il se comporte comme prévu.  
  
#### Pour tester le formulaire  
  
-   Compilez et exécutez l'application.  
  
     Vous observerez un contrôle <xref:System.Windows.Forms.DataGridView> rempli de trois enregistrements de client.  Vous pouvez modifier les valeurs de plusieurs cellules dans une ligne et appuyer deux fois sur ÉCHAP en mode édition, ou une fois dans un autre mode, pour redonner à toute la ligne ses valeurs d'origine.  Lorsque vous modifiez, ajoutez ou supprimez des lignes dans le contrôle, les objets `Customer` dans le magasin de données sont également modifiés, ajoutés ou supprimés.  
  
## Étapes suivantes  
 Cette application vous donne des notions de base sur les événements que vous devez gérer pour implémenter le mode virtuel dans le contrôle <xref:System.Windows.Forms.DataGridView>.  Vous pouvez améliorer cette application de base de plusieurs manières :  
  
-   Implémentez un magasin de données qui mette en cache des valeurs d'une base de données externe.  Le cache doit récupérer ou ignorer au besoin les valeurs de sorte qu'il ne contienne que les éléments devant être affichés tout en consommant une petite quantité de mémoire sur l'ordinateur client.  
  
-   Réglez avec précision la performance du magasin de données selon vos besoins.  Par exemple, vous pouvez chercher à compenser la lenteur des connexions réseau plutôt que les limitations de mémoire de l'ordinateur client en utilisant une taille de cache plus grande et en réduisant le nombre de requêtes de base de données.  
  
 Pour plus d'informations sur la mise en cache de valeurs à partir d'une base de données externe, consultez [Comment : implémenter le mode virtuel avec le chargement de données juste\-à\-temps dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md).  
  
## Voir aussi  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>   
 <xref:System.Windows.Forms.DataGridView.CellValueNeeded>   
 <xref:System.Windows.Forms.DataGridView.CellValuePushed>   
 <xref:System.Windows.Forms.DataGridView.NewRowNeeded>   
 <xref:System.Windows.Forms.DataGridView.RowValidated>   
 <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>   
 <xref:System.Windows.Forms.DataGridView.CancelRowEdit>   
 <xref:System.Windows.Forms.DataGridView.UserDeletingRow>   
 [Réglage des performances dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)   
 [Meilleures pratiques pour la mise à l'échelle du contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)   
 [Implémentation du mode virtuel avec le chargement de données juste\-à\-temps dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)   
 [Comment : implémenter le mode virtuel dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md)