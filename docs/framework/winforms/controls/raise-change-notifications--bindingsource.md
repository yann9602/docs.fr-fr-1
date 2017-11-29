---
title: "Comment : générer des notifications de modifications à l'aide d'un BindingSource et de l'interface INotifyPropertyChanged"
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
- change notifications [Windows Forms], raising
- BindingSource component [Windows Forms], and IPropertyChange
- data sources [Windows Forms], detecting changes
- examples [Windows Forms], BindingSource component
- change notifications
- INotifyPropertyChanged interface [Windows Forms], using with BindingSource
- BindingSource component [Windows Forms], examples
ms.assetid: 7fa2cf51-c09f-4375-adf0-e36c5617f099
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 049d87799e4ef241de0647815470cc853a29ea31
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-raise-change-notifications-using-a-bindingsource-and-the-inotifypropertychanged-interface"></a><span data-ttu-id="b2bf9-102">Comment : générer des notifications de modifications à l'aide d'un BindingSource et de l'interface INotifyPropertyChanged</span><span class="sxs-lookup"><span data-stu-id="b2bf9-102">How to: Raise Change Notifications Using a BindingSource and the INotifyPropertyChanged Interface</span></span>
<span data-ttu-id="b2bf9-103">Le composant <xref:System.Windows.Forms.BindingSource> détecte automatiquement les modifications apportées à une source de données quand le type contenu dans la source de données implémente l'interface <xref:System.ComponentModel.INotifyPropertyChanged> et déclenche des événements <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> quand une valeur de propriété est modifiée.</span><span class="sxs-lookup"><span data-stu-id="b2bf9-103">The <xref:System.Windows.Forms.BindingSource> component will automatically detect changes in a data source when the type contained in the data source implements the <xref:System.ComponentModel.INotifyPropertyChanged> interface and raises <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> events when a property value is changed.</span></span> <span data-ttu-id="b2bf9-104">Cela est utile, car les contrôles liés à <xref:System.Windows.Forms.BindingSource> sont alors automatiquement mis à jour en cas de modification des valeurs de la source de données.</span><span class="sxs-lookup"><span data-stu-id="b2bf9-104">This is useful because controls bound to the <xref:System.Windows.Forms.BindingSource> will then automatically update as the data source values change.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b2bf9-105">Si votre source de données implémente <xref:System.ComponentModel.INotifyPropertyChanged> et que vous exécutez des opérations asynchrones, vous ne devez pas modifier la source de données sur un thread d'arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="b2bf9-105">If your data source implements <xref:System.ComponentModel.INotifyPropertyChanged> and you are performing asynchronous operations, you should not make changes to the data source on a background thread.</span></span> <span data-ttu-id="b2bf9-106">Au lieu de cela, vous devez lire les données sur un thread d’arrière-plan et les fusionner dans une liste sur le thread d’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b2bf9-106">Instead, you should read the data on a background thread and merge the data into a list on the UI thread.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b2bf9-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="b2bf9-107">Example</span></span>  
 <span data-ttu-id="b2bf9-108">L'exemple de code suivant illustre une implémentation simple de l'interface <xref:System.ComponentModel.INotifyPropertyChanged>.</span><span class="sxs-lookup"><span data-stu-id="b2bf9-108">The following code example demonstrates a simple implementation of the <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span></span> <span data-ttu-id="b2bf9-109">Il montre également comment <xref:System.Windows.Forms.BindingSource> transmet automatiquement une modification de source de données à un contrôle lié quand <xref:System.Windows.Forms.BindingSource> est lié à une liste du type <xref:System.ComponentModel.INotifyPropertyChanged>.</span><span class="sxs-lookup"><span data-stu-id="b2bf9-109">It also shows how the <xref:System.Windows.Forms.BindingSource> automatically passes a data source change to a bound control when the <xref:System.Windows.Forms.BindingSource> is bound to a list of the <xref:System.ComponentModel.INotifyPropertyChanged> type.</span></span>  
  
 <span data-ttu-id="b2bf9-110">Si vous utilisez l'attribut `CallerMemberName`, les appels à la méthode `NotifyPropertyChanged` ne doivent pas obligatoirement spécifier le nom de la propriété comme argument de chaîne.</span><span class="sxs-lookup"><span data-stu-id="b2bf9-110">If you use the `CallerMemberName` attribute, calls to the `NotifyPropertyChanged` method don't have to specify the property name as a string argument.</span></span> <span data-ttu-id="b2bf9-111">Pour plus d’informations, consultez [informations d’appelant](http://msdn.microsoft.com/library/9cb2b8c0-c4f6-44b8-9c90-38948455b373).</span><span class="sxs-lookup"><span data-stu-id="b2bf9-111">For more information, see [Caller Information](http://msdn.microsoft.com/library/9cb2b8c0-c4f6-44b8-9c90-38948455b373).</span></span>  
  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b2bf9-112">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="b2bf9-112">Compiling the Code</span></span>  
 <span data-ttu-id="b2bf9-113">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="b2bf9-113">This example requires:</span></span>  
  
-   <span data-ttu-id="b2bf9-114">Références aux assemblys System, System.Data, System.Drawing et System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="b2bf9-114">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="b2bf9-115">Pour plus d’informations sur la création de cet exemple à partir de la ligne de commande pour [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], consultez [Génération à partir de la ligne de commande](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [Génération à partir de la ligne de commande avec csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="b2bf9-115">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="b2bf9-116">Vous pouvez également générer cet exemple dans [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] en collant le code dans un nouveau projet.</span><span class="sxs-lookup"><span data-stu-id="b2bf9-116">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="b2bf9-117">Consultez également [lien hypertexte « http://msdn.microsoft.com/library/Bb129228 (110) » Comment : compiler et exécuter un complète exemple Windows Forms Code à l’aide de Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="b2bf9-117">Also see [HYPERLINK "http://msdn.microsoft.com/library/Bb129228(v=vs.110)" How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2bf9-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b2bf9-118">See Also</span></span>  
 <xref:System.ComponentModel.INotifyPropertyChanged>  
 [<span data-ttu-id="b2bf9-119">BindingSource, composant</span><span class="sxs-lookup"><span data-stu-id="b2bf9-119">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [<span data-ttu-id="b2bf9-120">Comment : générer des notifications de modifications à l'aide de la méthode ResetItem de BindingSource</span><span class="sxs-lookup"><span data-stu-id="b2bf9-120">How to: Raise Change Notifications Using the BindingSource ResetItem Method</span></span>](../../../../docs/framework/winforms/controls/how-to-raise-change-notifications-using-the-bindingsource-resetitem-method.md)
