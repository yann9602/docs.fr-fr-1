---
title: "Comment&#160;: ajouter des donn&#233;es au Presse-papiers | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "Presse-papiers, copier les données dans"
  - "données (Windows Forms), copier dans le Presse-papiers"
ms.assetid: 25152454-0e78-40a9-8a9e-a2a5a274e517
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Comment&#160;: ajouter des donn&#233;es au Presse-papiers
La classe <xref:System.Windows.Forms.Clipboard> fournit des méthodes que vous pouvez utiliser pour interagir avec les fonctionnalités du Presse\-papiers du système d'exploitation Windows.  De nombreuses applications utilisent le Presse\-papiers en tant que référentiel temporaire pour les données.  Par exemple, les applications de traitement de texte utilisent le Presse\-papiers pour les opérations de copier\-coller.  Le Presse\-papiers est également utile pour transférer des données d'une application à une autre.  
  
 Lorsque vous ajoutez des données au Presse\-papiers, vous pouvez indiquer le format des données afin que d'autres applications puissent reconnaître les données lorsqu'elles peuvent utiliser ce format.  Vous pouvez également ajouter des données au Presse\-papiers dans différents formats pour augmenter le nombre d'autres applications susceptibles d'utiliser les données.  
  
 Un format de Presse\-papiers est une chaîne qui identifie le format afin qu'une application qui utilise ce format puisse récupérer les données associées.  La classe <xref:System.Windows.Forms.DataFormats> fournit des noms de formats prédéfinis que vous pouvez utiliser.  Vous pouvez également utiliser vos propres noms de formats ou le type d'un objet comme son format.  
  
 Pour ajouter des données au Presse\-papiers dans un ou plusieurs formats, utilisez la méthode <xref:System.Windows.Forms.Clipboard.SetDataObject%2A>.  Vous pouvez passer n'importe quel objet à cette méthode, mais pour ajouter des données dans plusieurs formats, vous devez d'abord les ajouter dans un objet distinct conçu pour utiliser des formats multiples.  En général, vous ajouterez vos données à un <xref:System.Windows.Forms.DataObject>, mais vous pouvez utiliser n'importe quel type qui implémente l'interface <xref:System.Windows.Forms.IDataObject>.  
  
 Dans [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)], vous pouvez ajouter directement des données au Presse\-papiers en utilisant de nouvelles méthodes conçues pour simplifier les tâches de base du Presse\-papiers.  Utilisez ces méthodes lorsque vous utilisez des données dans un seul format commun tel que le format texte.  
  
> [!NOTE]
>  Toutes les applications Windows partagent le Presse\-papiers.  Par conséquent, le contenu est susceptible de changer lorsque vous basculez vers une autre application.  
>   
>  La classe <xref:System.Windows.Forms.Clipboard> peut être utilisée uniquement dans les threads configurés en mode STA \(Single Thread Apartment\).  Pour utiliser cette classe, veillez à ce que votre méthode `Main` soit marquée avec l'attribut <xref:System.STAThreadAttribute>.  
>   
>  Un objet doit être sérialisable pour être placé dans le Presse\-papiers.  Pour rendre un type sérialisable, marquez\-le avec l'attribut <xref:System.SerializableAttribute>.  Si vous passez un objet non sérialisable à une méthode Clipboard, la méthode échouera sans lever une exception.  Pour plus d'informations sur la sérialisation, consultez <xref:System.Runtime.Serialization>.  
  
### Pour ajouter des données au Presse\-papiers dans un seul format commun  
  
1.  Utilisez la méthode <xref:System.Windows.Forms.Clipboard.SetAudio%2A>, <xref:System.Windows.Forms.Clipboard.SetFileDropList%2A>, <xref:System.Windows.Forms.Clipboard.SetImage%2A> ou <xref:System.Windows.Forms.Clipboard.SetText%2A>.  Ces méthodes sont disponibles uniquement dans [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].  
  
     [!code-csharp[System.Windows.Forms.Clipboard#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.Clipboard#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#2)]  
  
### Pour ajouter des données au Presse\-papiers dans un format personnalisé  
  
1.  Utilisez la méthode <xref:System.Windows.Forms.Clipboard.SetData%2A> avec un nom de format personnalisé.  Cette méthode est uniquement disponible dans [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].  
  
     Vous pouvez également utiliser des noms de formats prédéfinis avec la méthode <xref:System.Windows.Forms.Clipboard.SetData%2A>.  Pour plus d'informations, consultez <xref:System.Windows.Forms.DataFormats>.  
  
     [!code-csharp[System.Windows.Forms.Clipboard#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.Clipboard#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#3)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
### Pour ajouter des données au Presse\-papiers dans plusieurs formats  
  
1.  Utilisez la méthode <xref:System.Windows.Forms.Clipboard.SetDataObject%2A> et passez\-la dans un <xref:System.Windows.Forms.DataObject> qui contient vos données.  Vous devez utiliser cette méthode pour ajouter des données au Presse\-papiers sur les versions précédentes du [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)].  
  
     [!code-csharp[System.Windows.Forms.Clipboard#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.Clipboard#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#4)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
## Voir aussi  
 [Opérations glisser\-déplacer et prise en charge du Presse\-papiers](../../../../docs/framework/winforms/advanced/drag-and-drop-operations-and-clipboard-support.md)   
 [Comment : récupérer des données du Presse\-papiers](../../../../docs/framework/winforms/advanced/how-to-retrieve-data-from-the-clipboard.md)