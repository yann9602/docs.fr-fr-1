---
title: "Comment : convertir des données liées"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- converting [WPF], bound data
- data binding [WPF], converting bound data
- binding data [WPF], converting bound data
ms.assetid: b00aaa19-c6df-4c3b-a9fd-88a0b488df2b
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 88e248c7c8e60fbe8e55567cb642200820b25214
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-convert-bound-data"></a><span data-ttu-id="0a563-102">Comment : convertir des données liées</span><span class="sxs-lookup"><span data-stu-id="0a563-102">How to: Convert Bound Data</span></span>
<span data-ttu-id="0a563-103">Cet exemple montre comment appliquer la conversion de données qui sont utilisées dans les liaisons.</span><span class="sxs-lookup"><span data-stu-id="0a563-103">This example shows how to apply conversion to data that is used in bindings.</span></span>  
  
 <span data-ttu-id="0a563-104">Pour convertir des données lors de la liaison, vous devez créer une classe qui implémente le <xref:System.Windows.Data.IValueConverter> interface, qui inclut le <xref:System.Windows.Data.IValueConverter.Convert%2A> et <xref:System.Windows.Data.IValueConverter.ConvertBack%2A> méthodes.</span><span class="sxs-lookup"><span data-stu-id="0a563-104">To convert data during binding, you must create a class that implements the <xref:System.Windows.Data.IValueConverter> interface, which includes the <xref:System.Windows.Data.IValueConverter.Convert%2A> and <xref:System.Windows.Data.IValueConverter.ConvertBack%2A> methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0a563-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="0a563-105">Example</span></span>  
 <span data-ttu-id="0a563-106">L’exemple suivant illustre l’implémentation d’un convertisseur de date qui convertit la valeur de date passée pour qu’il affiche uniquement l’année, mois et jour.</span><span class="sxs-lookup"><span data-stu-id="0a563-106">The following example shows the implementation of a date converter that converts the date value passed in so that it only shows the year, the month, and the day.</span></span> <span data-ttu-id="0a563-107">Lorsque vous implémentez le <xref:System.Windows.Data.IValueConverter> interface, il est conseillé de décorer l’implémentation avec un <xref:System.Windows.Data.ValueConversionAttribute> attribut pour indiquer au développement d’outils de types de données impliqués dans la conversion, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="0a563-107">When implementing the <xref:System.Windows.Data.IValueConverter> interface, it is a good practice to decorate the implementation with a <xref:System.Windows.Data.ValueConversionAttribute> attribute to indicate to development tools the data types involved in the conversion, as in the following example:</span></span>  
  
 [!code-csharp[DataBindingLab#18](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DateConverter.cs#18)]
 [!code-vb[DataBindingLab#18](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/DateConverter.vb#18)]  
  
 <span data-ttu-id="0a563-108">Une fois que vous avez créé un convertisseur, vous pouvez l’ajouter en tant que ressource dans votre [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] fichier.</span><span class="sxs-lookup"><span data-stu-id="0a563-108">Once you have created a converter, you can add it as a resource in your [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file.</span></span> <span data-ttu-id="0a563-109">Dans l’exemple suivant, *src* est mappé à l’espace de noms dans lequel *convertisseur de date* est défini.</span><span class="sxs-lookup"><span data-stu-id="0a563-109">In the following example, *src* maps to the namespace in which *DateConverter* is defined.</span></span>  
  
 [!code-xaml[DataBindingLab#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#15)]  
  
 <span data-ttu-id="0a563-110">Enfin, vous pouvez utiliser le convertisseur dans votre liaison à l’aide de la syntaxe suivante.</span><span class="sxs-lookup"><span data-stu-id="0a563-110">Finally, you can use the converter in your binding using the following syntax.</span></span> <span data-ttu-id="0a563-111">Dans l’exemple suivant, le contenu textuel de la <xref:System.Windows.Controls.TextBlock> est lié à *StartDate*, qui est une propriété de source de données externe.</span><span class="sxs-lookup"><span data-stu-id="0a563-111">In the following example, the text content of the <xref:System.Windows.Controls.TextBlock> is bound to *StartDate*, which is a property of an external data source.</span></span>  
  
 [!code-xaml[DataBindingLab#17](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#17)]  
  
 <span data-ttu-id="0a563-112">Les ressources de style référencées dans l’exemple ci-dessus sont définies dans une section de ressources ne pas présentée dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="0a563-112">The style resources referenced in the above example are defined in a resource section not shown in this topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a563-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0a563-113">See Also</span></span>  
 [<span data-ttu-id="0a563-114">Implémenter la validation de la liaison</span><span class="sxs-lookup"><span data-stu-id="0a563-114">Implement Binding Validation</span></span>](../../../../docs/framework/wpf/data/how-to-implement-binding-validation.md)  
 [<span data-ttu-id="0a563-115">Vue d’ensemble de la liaison de données</span><span class="sxs-lookup"><span data-stu-id="0a563-115">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="0a563-116">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="0a563-116">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
