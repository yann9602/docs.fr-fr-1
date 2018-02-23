---
title: "Comment : créer une liaison simple"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- simple binding [WPF], creating
- data binding [WPF], creating simple bindings
- binding data [WPF], creating
ms.assetid: 69b80f72-6259-44cb-8294-5bdcebca1e08
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a595f255b014e08b4b5b2036a7b1940e46df268f
ms.sourcegitcommit: 973a12d1e6962cd9a9c263fbfaad040ec8267fe9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2018
---
# <a name="how-to-create-a-simple-binding"></a>Comment : créer une liaison simple
Cet exemple vous montre comment créer un simple <xref:System.Windows.Data.Binding>.  
  
## <a name="example"></a>Exemple  
 Dans cet exemple, vous avez un `Person` objet avec une propriété de chaîne nommée `PersonName`. Le `Person` objet est défini dans l’espace de noms appelé `SDKSample`.  
  
 En surbrillance la ligne qui contient le `<src>` élément dans l’exemple suivant instancie le `Person` de l’objet avec un `PersonName` valeur de propriété `Joe`. Cette opération est effectuée le `Resources` section et affecté un `x:Key`.  
  
 [!code-xaml[SimpleBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 La ligne en surbrillance qui contient le `<TextBlock>` élément puis lie la <xref:System.Windows.Controls.TextBlock> le contrôle à la `PersonName` propriété. Par conséquent, le <xref:System.Windows.Controls.TextBlock> apparaît avec la valeur « Joe ».  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Rubriques de guide pratique](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
