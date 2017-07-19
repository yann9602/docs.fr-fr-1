---
title: "Comment&#160;: r&#233;cup&#233;rer des donn&#233;es du Presse-papiers | Microsoft Docs"
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
  - "Presse-papiers, récupérer des données"
  - "coller les données du Presse-papiers"
ms.assetid: 99612537-2c8a-449f-aab5-2b3b28d656e7
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Comment&#160;: r&#233;cup&#233;rer des donn&#233;es du Presse-papiers
La classe <xref:System.Windows.Forms.Clipboard> fournit des méthodes que vous pouvez utiliser pour interagir avec les fonctionnalités du Presse\-papiers du système d'exploitation Windows.  De nombreuses applications utilisent le Presse\-papiers en tant que référentiel temporaire pour les données.  Par exemple, les applications de traitement de texte utilisent le Presse\-papiers pour les opérations de copier\-coller.  Le Presse\-papiers est également utile pour transférer des informations d'une application à un autre.  
  
 Certaines applications stockent des données dans le Presse\-papiers dans plusieurs formats pour augmenter le nombre d'applications capables d'utiliser les données.  Un format de Presse\-papiers est une chaîne qui identifie le format.  Une application qui utilise le format identifié peut récupérer les données associées sur le Presse\-papiers.  La classe <xref:System.Windows.Forms.DataFormats> fournit des noms de formats prédéfinis que vous pouvez utiliser.  Vous pouvez également utiliser vos propres noms de formats ou le type d'un objet comme son format.  Pour plus d'informations sur l'ajout de données dans le Presse\-papiers, consultez [Comment : ajouter des données au Presse\-papiers](../../../../docs/framework/winforms/advanced/how-to-add-data-to-the-clipboard.md).  
  
 Pour déterminer si le Presse\-papiers contient des données dans un format particulier, utilisez une des méthodes `Contains`*Format* ou la méthode <xref:System.Windows.Forms.Clipboard.GetData%2A>.  Pour récupérer des données du Presse\-papiers, utilisez une des méthodes `Get`*Format* ou la méthode <xref:System.Windows.Forms.Clipboard.GetData%2A>.  Ces méthodes sont nouvelles dans [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].  
  
 Pour accéder aux données du Presse\-papiers en utilisant les versions précédentes du [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)], utilisez la méthode <xref:System.Windows.Forms.Clipboard.GetDataObject%2A> et appelez les méthodes de l'<xref:System.Windows.Forms.IDataObject> retourné.  Pour déterminer si un format particulier est disponible dans l'objet retourné, par exemple, appelez la méthode <xref:System.Windows.Forms.IDataObject.GetDataPresent%2A>.  
  
> [!NOTE]
>  Toutes les applications Windows partagent le Presse\-papiers du système.  Par conséquent, le contenu est susceptible de changer lorsque vous basculez vers une autre application.  
>   
>  La classe <xref:System.Windows.Forms.Clipboard> peut être utilisée uniquement dans les threads configurés en mode STA \(Single Thread Apartment\).  Pour utiliser cette classe, veillez à ce que votre méthode `Main` soit marquée avec l'attribut <xref:System.STAThreadAttribute>.  
  
### Pour récupérer des données du Presse\-papiers dans un format commun unique  
  
1.  Utilisez la méthode <xref:System.Windows.Forms.Clipboard.GetAudioStream%2A>, <xref:System.Windows.Forms.Clipboard.GetFileDropList%2A>, <xref:System.Windows.Forms.Clipboard.GetImage%2A> ou <xref:System.Windows.Forms.Clipboard.GetText%2A>.  Si vous le souhaitez, vous pouvez utiliser les méthodes `Contains`*Format* correspondantes afin de déterminer si les données sont disponibles dans un format particulier.  Ces méthodes sont disponibles uniquement dans [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].  
  
     [!code-csharp[System.Windows.Forms.Clipboard#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.Clipboard#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#2)]  
  
### Pour récupérer des données du Presse\-papiers dans un format personnalisé  
  
1.  Utilisez la méthode <xref:System.Windows.Forms.Clipboard.GetData%2A> avec un nom de format personnalisé.  Cette méthode est uniquement disponible dans [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].  
  
     Vous pouvez également utiliser des noms de formats prédéfinis avec la méthode <xref:System.Windows.Forms.Clipboard.SetData%2A>.  Pour plus d'informations, consultez <xref:System.Windows.Forms.DataFormats>.  
  
     [!code-csharp[System.Windows.Forms.Clipboard#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.Clipboard#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#3)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
### Pour récupérer des données du Presse\-papiers dans des formats multiples  
  
1.  Utilisez la méthode <xref:System.Windows.Forms.Clipboard.GetDataObject%2A>.  Vous devez utiliser cette méthode pour récupérer des données du Presse\-papiers sur les versions précédentes du [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)].  
  
     [!code-csharp[System.Windows.Forms.Clipboard#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.Clipboard#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#4)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
## Voir aussi  
 [Opérations glisser\-déplacer et prise en charge du Presse\-papiers](../../../../docs/framework/winforms/advanced/drag-and-drop-operations-and-clipboard-support.md)   
 [Comment : ajouter des données au Presse\-papiers](../../../../docs/framework/winforms/advanced/how-to-add-data-to-the-clipboard.md)