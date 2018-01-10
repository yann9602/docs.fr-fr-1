---
title: "Vue d'ensemble du contrôle PrintPreviewDialog (Windows Forms)"
ms.custom: 
ms.date: 01/08/2018
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: PrintPreviewDialog
helpviewer_keywords: PrintPreviewDialog control (using designer), about PrintPreviewDialog
ms.assetid: efd4ee8d-6edd-47ec-88e4-4a4759bd2384
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1228a3cf39ea412cde341c4c4b8b83e0ab2f0299
ms.sourcegitcommit: 91691981897cf8451033cb01071d8f5d94017f97
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/09/2018
---
# <a name="printpreviewdialog-control-overview-windows-forms"></a><span data-ttu-id="6e50e-102">Vue d’ensemble du contrôle PrintPreviewDialog (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="6e50e-102">PrintPreviewDialog control overview (Windows Forms)</span></span>
<span data-ttu-id="6e50e-103">Windows Forms <xref:System.Windows.Forms.PrintPreviewDialog> contrôle est une boîte de dialogue préconfigurée permettant d’afficher comment un [PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) apparaîtra une fois imprimé.</span><span class="sxs-lookup"><span data-stu-id="6e50e-103">The Windows Forms <xref:System.Windows.Forms.PrintPreviewDialog> control is a pre-configured dialog box used to display how a [PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) will appear when printed.</span></span> <span data-ttu-id="6e50e-104">Utiliser dans votre application Windows comme une solution simple au lieu de configurer votre propre boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="6e50e-104">Use it within your Windows-based application as a simple solution instead of configuring your own dialog box.</span></span> <span data-ttu-id="6e50e-105">Le contrôle contient des boutons pour l'impression, le zoom avant, l'affichage d'une ou plusieurs pages et la fermeture de la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="6e50e-105">The control contains buttons for printing, zooming in, displaying one or multiple pages, and closing the dialog box.</span></span>  
  
## <a name="key-properties-and-methods"></a><span data-ttu-id="6e50e-106">Méthodes et propriétés de clé</span><span class="sxs-lookup"><span data-stu-id="6e50e-106">Key properties and methods</span></span>  
 <span data-ttu-id="6e50e-107">Propriété de clé du contrôle <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A>, qui définit le document à afficher.</span><span class="sxs-lookup"><span data-stu-id="6e50e-107">The control's key property is <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A>, which sets the document to be previewed.</span></span> <span data-ttu-id="6e50e-108">Le document doit être un <xref:System.Drawing.Printing.PrintDocument> objet.</span><span class="sxs-lookup"><span data-stu-id="6e50e-108">The document must be a <xref:System.Drawing.Printing.PrintDocument> object.</span></span> <span data-ttu-id="6e50e-109">Pour afficher la boîte de dialogue, vous devez appeler sa <xref:System.Windows.Forms.Form.ShowDialog%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="6e50e-109">In order to display the dialog box, you must call its <xref:System.Windows.Forms.Form.ShowDialog%2A> method.</span></span> <span data-ttu-id="6e50e-110">L’anticrénelage peut lisser le texte, mais il peut également apporter de ralentir l’affichage ; pour l’utiliser, définissez la <xref:System.Windows.Forms.PrintPreviewDialog.UseAntiAlias%2A> propriété `true`.</span><span class="sxs-lookup"><span data-stu-id="6e50e-110">Anti-aliasing can make the text appear smoother, but it can also make the display slower; to use it, set the <xref:System.Windows.Forms.PrintPreviewDialog.UseAntiAlias%2A> property to `true`.</span></span>  
  
 <span data-ttu-id="6e50e-111">Certaines propriétés sont disponibles via le <xref:System.Windows.Forms.PrintPreviewControl> qui le <xref:System.Windows.Forms.PrintPreviewDialog> contient.</span><span class="sxs-lookup"><span data-stu-id="6e50e-111">Certain properties are available through the <xref:System.Windows.Forms.PrintPreviewControl> that the <xref:System.Windows.Forms.PrintPreviewDialog> contains.</span></span> <span data-ttu-id="6e50e-112">(Vous n’avez pas à l’ajouter <xref:System.Windows.Forms.PrintPreviewControl> au formulaire ; il est automatiquement contenu dans le <xref:System.Windows.Forms.PrintPreviewDialog> lorsque vous ajoutez la boîte de dialogue à votre formulaire.) Les propriétés disponibles via le <xref:System.Windows.Forms.PrintPreviewControl> sont les <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> et <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> qui déterminent le nombre de pages affichées horizontalement et verticalement sur le contrôle.</span><span class="sxs-lookup"><span data-stu-id="6e50e-112">(You do not have to add this <xref:System.Windows.Forms.PrintPreviewControl> to the form; it is automatically contained within the <xref:System.Windows.Forms.PrintPreviewDialog> when you add the dialog to your form.) Examples of properties available through the <xref:System.Windows.Forms.PrintPreviewControl> are the <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> and <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> properties, which determine the number of pages displayed horizontally and vertically on the control.</span></span> <span data-ttu-id="6e50e-113">Vous pouvez accéder à la <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> propriété en tant que `PrintPreviewDialog1.PrintPreviewControl.Columns` dans [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], `printPreviewDialog1.PrintPreviewControl.Columns` dans [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], ou `printPreviewDialog1->PrintPreviewControl->Columns` dans [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6e50e-113">You can access the <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> property as `PrintPreviewDialog1.PrintPreviewControl.Columns` in [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], `printPreviewDialog1.PrintPreviewControl.Columns` in [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], or `printPreviewDialog1->PrintPreviewControl->Columns` in [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)].</span></span>  
  
## <a name="printpreviewdialog-performance"></a><span data-ttu-id="6e50e-114">Performances de PrintPreviewDialog</span><span class="sxs-lookup"><span data-stu-id="6e50e-114">PrintPreviewDialog performance</span></span>

<span data-ttu-id="6e50e-115">Dans les conditions suivantes, le <xref:System.Windows.Forms.PrintPreviewDialog> contrôle initialise très lentement :</span><span class="sxs-lookup"><span data-stu-id="6e50e-115">Under the following conditions, the <xref:System.Windows.Forms.PrintPreviewDialog> control initializes very slowly:</span></span>

- <span data-ttu-id="6e50e-116">Une imprimante réseau est utilisée.</span><span class="sxs-lookup"><span data-stu-id="6e50e-116">A network printer is used.</span></span>
- <span data-ttu-id="6e50e-117">Préférences utilisateur pour cette imprimante, telles que les paramètres duplex sont modifiées.</span><span class="sxs-lookup"><span data-stu-id="6e50e-117">User preferences for this printer, such as duplex settings, are modified.</span></span>
  
<span data-ttu-id="6e50e-118">Pour les applications en cours d’exécution sur le .NET Framework 4.5.2, vous pouvez ajouter la clé suivante à la \<appSettings > section de votre fichier de configuration pour améliorer les performances de <xref:System.Windows.Forms.PrintPreviewDialog> contrôlent l’initialisation :</span><span class="sxs-lookup"><span data-stu-id="6e50e-118">For apps running on the .NET Framework 4.5.2, you can add the following key to the \<appSettings> section of your configuration file to improve the performance of <xref:System.Windows.Forms.PrintPreviewDialog> control initialization:</span></span>

```xml
<appSettings>
   <add key="EnablePrintPreviewOptimization" value="true" />
</appSettings>
```
<span data-ttu-id="6e50e-119">Si le `EnablePrintPreviewOptimization` clé est définie sur toute autre valeur, ou si la clé n’est pas présente, l’optimisation n’est pas appliquée.</span><span class="sxs-lookup"><span data-stu-id="6e50e-119">If the `EnablePrintPreviewOptimization` key is set to any other value, or if the key is not present, the optimization is not applied.</span></span>

<span data-ttu-id="6e50e-120">Pour les applications en cours d’exécution sur le .NET Framework 4.6 ou versions ultérieures, vous pouvez ajouter le commutateur suivant à la [ \<AppContextSwitchOverrides >](../../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) élément dans le [ \<runtime >](../../configure-apps/file-schema/runtime/index.md) section de votre fichier de configuration d’application :</span><span class="sxs-lookup"><span data-stu-id="6e50e-120">For apps running on the .NET Framework 4.6 or later versions, you can add the following switch to the [\<AppContextSwitchOverrides>](../../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [\<runtime>](../../configure-apps/file-schema/runtime/index.md) section of your app config file:</span></span>

```xml
<runtime >
   <!-- AppContextSwitchOverrides values are in the form of 'key1=true|false;key2=true|false -->
   <AppContextSwitchOverrides value = "Switch.System.Drawing.Printing.OptimizePrintPreview=true" />
</runtime >
``` 
<span data-ttu-id="6e50e-121">Si le commutateur n’est pas présent ou si elle est définie sur toute autre valeur, l’optimisation n’est pas appliquée.</span><span class="sxs-lookup"><span data-stu-id="6e50e-121">If the switch is not present or if it is set to any other value, the optimization is not applied.</span></span> 

<span data-ttu-id="6e50e-122">Si vous utilisez la <xref:System.Drawing.Printing.PrintDocument.QueryPageSettings> événement pour modifier les paramètres d’imprimante, les performances de la <xref:System.Windows.Forms.PrintPreviewDialog> contrôle n’améliorera pas même si un commutateur de configuration de l’optimisation est défini.</span><span class="sxs-lookup"><span data-stu-id="6e50e-122">If you use the <xref:System.Drawing.Printing.PrintDocument.QueryPageSettings> event to modify printer settings, the performance of the <xref:System.Windows.Forms.PrintPreviewDialog> control will not improve even if an optimization configuration switch is set.</span></span>  

## <a name="see-also"></a><span data-ttu-id="6e50e-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6e50e-123">See also</span></span>  
 <xref:System.Windows.Forms.PrintPreviewDialog>  
 [<span data-ttu-id="6e50e-124">Vue d’ensemble du contrôle PrintPreviewControl</span><span class="sxs-lookup"><span data-stu-id="6e50e-124">PrintPreviewControl Control Overview</span></span>](../../../../docs/framework/winforms/controls/printpreviewcontrol-control-overview-windows-forms.md)  
 [<span data-ttu-id="6e50e-125">PrintPreviewDialog, contrôle</span><span class="sxs-lookup"><span data-stu-id="6e50e-125">PrintPreviewDialog Control</span></span>](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)  
 [<span data-ttu-id="6e50e-126">Contrôles et composants de boîte de dialogue</span><span class="sxs-lookup"><span data-stu-id="6e50e-126">Dialog-Box Controls and Components</span></span>](../../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md)
