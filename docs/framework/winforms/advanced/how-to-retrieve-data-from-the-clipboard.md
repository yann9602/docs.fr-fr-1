---
title: "Comment : récupérer des données du Presse-papiers"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pasting Clipboard data
- Clipboard [Windows Forms], retrieving data
ms.assetid: 99612537-2c8a-449f-aab5-2b3b28d656e7
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c2f71c6738f19e70826b95626377097de0cd9b3b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-retrieve-data-from-the-clipboard"></a>Comment : récupérer des données du Presse-papiers
La <xref:System.Windows.Forms.Clipboard> classe fournit des méthodes que vous pouvez utiliser pour interagir avec la fonctionnalité du Presse-papiers du système d’exploitation Windows. De nombreuses applications utilisent le Presse-papiers comme référentiel temporaire pour les données. Par exemple, les traitements utiliser le Presse-papiers lors des opérations de couper-coller. Le Presse-papiers est également utile pour transférer des informations d’une application vers un autre.  
  
 Certaines applications stockent des données dans le Presse-papiers dans plusieurs formats pour augmenter le nombre d’autres applications qui peut utiliser les données. Un format de Presse-papiers est une chaîne qui identifie le format. Une application qui utilise le format identifié peut récupérer les données associées dans le Presse-papiers. La <xref:System.Windows.Forms.DataFormats> classe fournit les noms de formats prédéfinis pour votre utilisation. Vous pouvez également utiliser vos propres noms de format ou utiliser un type d’objet en tant que son format. Pour plus d’informations sur l’ajout de données dans le Presse-papiers, consultez [Comment : ajouter des données dans le Presse-papiers](../../../../docs/framework/winforms/advanced/how-to-add-data-to-the-clipboard.md).  
  
 Pour déterminer si le Presse-papiers contient des données dans un format particulier, utilisez une de la `Contains` *Format* méthodes ou <xref:System.Windows.Forms.Clipboard.GetData%2A> (méthode). Pour récupérer des données à partir du Presse-papiers, utilisez une de la `Get` *Format* méthodes ou <xref:System.Windows.Forms.Clipboard.GetData%2A> (méthode). Ces méthodes sont nouvelles dans [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].  
  
 Pour accéder aux données à partir du Presse-papiers à l’aide de versions antérieures à [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)], utilisez le <xref:System.Windows.Forms.Clipboard.GetDataObject%2A> (méthode) et appeler les méthodes de retourné <xref:System.Windows.Forms.IDataObject>. Pour déterminer si un format particulier est disponible dans l’objet retourné, par exemple, appelez le <xref:System.Windows.Forms.IDataObject.GetDataPresent%2A> (méthode).  
  
> [!NOTE]
>  Toutes les applications Windows partagent le Presse-papiers du système. Par conséquent, le contenu est susceptible de changer lorsque vous basculez vers une autre application.  
>   
>  La <xref:System.Windows.Forms.Clipboard> classe peut uniquement être utilisée dans les threads en mode thread unique cloisonné (STA). Pour utiliser cette classe, assurez-vous que votre `Main` méthode est marquée avec le <xref:System.STAThreadAttribute> attribut.  
  
### <a name="to-retrieve-data-from-the-clipboard-in-a-single-common-format"></a>Pour récupérer des données à partir du Presse-papiers dans un format commun unique  
  
1.  Utilisez le <xref:System.Windows.Forms.Clipboard.GetAudioStream%2A>, <xref:System.Windows.Forms.Clipboard.GetFileDropList%2A>, <xref:System.Windows.Forms.Clipboard.GetImage%2A>, ou <xref:System.Windows.Forms.Clipboard.GetText%2A> (méthode). Si vous le souhaitez, utilisez la `Contains` *Format* méthodes afin de déterminer si les données sont disponibles dans un format particulier. Ces méthodes sont disponibles uniquement dans [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].  
  
     [!code-csharp[System.Windows.Forms.Clipboard#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.Clipboard#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#2)]  
  
### <a name="to-retrieve-data-from-the-clipboard-in-a-custom-format"></a>Pour récupérer des données à partir du Presse-papiers dans un format personnalisé  
  
1.  Utilisez la <xref:System.Windows.Forms.Clipboard.GetData%2A> méthode avec un nom de format personnalisé. Cette méthode est uniquement disponible dans [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].  
  
     Vous pouvez également utiliser des noms de formats prédéfinis avec la <xref:System.Windows.Forms.Clipboard.SetData%2A> (méthode). Pour plus d'informations, consultez <xref:System.Windows.Forms.DataFormats>.  
  
     [!code-csharp[System.Windows.Forms.Clipboard#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.Clipboard#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#3)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
### <a name="to-retrieve-data-from-the-clipboard-in-multiple-formats"></a>Pour récupérer des données à partir du Presse-papiers dans plusieurs formats  
  
1.  Utilisez la méthode <xref:System.Windows.Forms.Clipboard.GetDataObject%2A>. Vous devez utiliser cette méthode pour récupérer des données à partir du Presse-papiers dans les versions antérieures à [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)].  
  
     [!code-csharp[System.Windows.Forms.Clipboard#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.Clipboard#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#4)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
## <a name="see-also"></a>Voir aussi  
 [Opérations glisser-déposer et prise en charge du Presse-papiers](../../../../docs/framework/winforms/advanced/drag-and-drop-operations-and-clipboard-support.md)  
 [Guide pratique pour ajouter des données au Presse-papiers](../../../../docs/framework/winforms/advanced/how-to-add-data-to-the-clipboard.md)
