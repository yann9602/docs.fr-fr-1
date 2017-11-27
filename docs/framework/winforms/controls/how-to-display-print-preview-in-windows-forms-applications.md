---
title: "Comment : afficher l’aperçu avant impression dans les applications Windows Forms"
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
- cpp
helpviewer_keywords:
- print preview [Windows Forms], displaying
- printing [Windows Forms], print preview
- examples [Windows Forms], print preview
ms.assetid: e394134c-0886-4517-bd8d-edc4a3749eb5
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e705575b8c3acdcc3d92b985c59b60e7310dce7b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-print-preview-in-windows-forms-applications"></a><span data-ttu-id="225aa-102">Comment : afficher l’aperçu avant impression dans les applications Windows Forms</span><span class="sxs-lookup"><span data-stu-id="225aa-102">How to: Display Print Preview in Windows Forms Applications</span></span>
<span data-ttu-id="225aa-103">Vous pouvez utiliser la <xref:System.Windows.Forms.PrintPreviewDialog> contrôle pour permettre aux utilisateurs d’afficher un document, souvent avant qu’il soit à imprimer.</span><span class="sxs-lookup"><span data-stu-id="225aa-103">You can use the <xref:System.Windows.Forms.PrintPreviewDialog> control to enable users to display a document, often before it is to be printed.</span></span>  
  
 <span data-ttu-id="225aa-104">Pour ce faire, vous devez spécifier une instance de la <xref:System.Drawing.Printing.PrintDocument> classe ; il s’agit du document à imprimer.</span><span class="sxs-lookup"><span data-stu-id="225aa-104">To do this, you need to specify an instance of the <xref:System.Drawing.Printing.PrintDocument> class; this is the document to be printed.</span></span> <span data-ttu-id="225aa-105">Pour plus d’informations sur l’utilisation de l’aperçu avant impression avec le <xref:System.Drawing.Printing.PrintDocument> composant, consultez [Comment : imprimer dans les Windows Forms à l’aide d’Aperçu avant impression](../../../../docs/framework/winforms/advanced/how-to-print-in-windows-forms-using-print-preview.md).</span><span class="sxs-lookup"><span data-stu-id="225aa-105">For more information about using print preview with the <xref:System.Drawing.Printing.PrintDocument> component, see [How to: Print in Windows Forms Using Print Preview](../../../../docs/framework/winforms/advanced/how-to-print-in-windows-forms-using-print-preview.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="225aa-106">Pour utiliser le <xref:System.Windows.Forms.PrintPreviewDialog> contrôle au moment de l’exécution, les utilisateurs doivent disposer d’imprimante installée sur son ordinateur, localement ou via un réseau, car il s’agit en partie la <xref:System.Windows.Forms.PrintPreviewDialog> composant détermine à quoi ressemblera un document lors de l’impression.</span><span class="sxs-lookup"><span data-stu-id="225aa-106">To use the <xref:System.Windows.Forms.PrintPreviewDialog> control at run time, users must have a printer installed on their computer, either locally or through a network, as this is partly how the <xref:System.Windows.Forms.PrintPreviewDialog> component determines how a document will look when printed.</span></span>  
  
 <span data-ttu-id="225aa-107">Le <xref:System.Windows.Forms.PrintPreviewDialog> de contrôles utilise la <xref:System.Drawing.Printing.PrinterSettings> classe.</span><span class="sxs-lookup"><span data-stu-id="225aa-107">The <xref:System.Windows.Forms.PrintPreviewDialog> control uses the <xref:System.Drawing.Printing.PrinterSettings> class.</span></span> <span data-ttu-id="225aa-108">En outre, le <xref:System.Windows.Forms.PrintPreviewDialog> de contrôles utilise la <xref:System.Drawing.Printing.PageSettings> (classe), tout comme le <xref:System.Windows.Forms.PrintPreviewDialog> du composant.</span><span class="sxs-lookup"><span data-stu-id="225aa-108">Additionally, the <xref:System.Windows.Forms.PrintPreviewDialog> control uses the <xref:System.Drawing.Printing.PageSettings> class, just as the <xref:System.Windows.Forms.PrintPreviewDialog> component does.</span></span> <span data-ttu-id="225aa-109">Le document d’impression spécifié dans le <xref:System.Windows.Forms.PrintPreviewDialog> du contrôle <xref:System.Windows.Forms.PrintPreviewControl.Document%2A> propriété fait référence à des instances de la <xref:System.Drawing.Printing.PrinterSettings> et <xref:System.Drawing.Printing.PageSettings> classes et ils sont utilisés pour afficher le document dans la fenêtre d’aperçu.</span><span class="sxs-lookup"><span data-stu-id="225aa-109">The print document specified in the <xref:System.Windows.Forms.PrintPreviewDialog> control's <xref:System.Windows.Forms.PrintPreviewControl.Document%2A> property refers to instances of both the <xref:System.Drawing.Printing.PrinterSettings> and <xref:System.Drawing.Printing.PageSettings> classes, and these are used to render the document in the preview window.</span></span>  
  
### <a name="to-view-pages-using-the-printpreviewdialog-control"></a><span data-ttu-id="225aa-110">Pour afficher des pages à l’aide du contrôle PrintPreviewDialog</span><span class="sxs-lookup"><span data-stu-id="225aa-110">To view pages using the PrintPreviewDialog control</span></span>  
  
-   <span data-ttu-id="225aa-111">Utilisez la méthode <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> pour afficher la boîte de dialogue, en spécifiant le <xref:System.Drawing.Printing.PrintDocument> à utiliser.</span><span class="sxs-lookup"><span data-stu-id="225aa-111">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog box, specifying the <xref:System.Drawing.Printing.PrintDocument> to use.</span></span>  
  
     <span data-ttu-id="225aa-112">Dans l’exemple de code suivant, le <xref:System.Windows.Forms.Button> du contrôle <xref:System.Windows.Forms.Control.Click> Gestionnaire d’événements ouvre une instance de la <xref:System.Windows.Forms.PrintPreviewDialog> contrôle.</span><span class="sxs-lookup"><span data-stu-id="225aa-112">In the following code example, the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler opens an instance of the <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span> <span data-ttu-id="225aa-113">Le document d’impression est spécifié dans le <xref:System.Windows.Forms.PrintDialog.Document%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="225aa-113">The print document is specified in the <xref:System.Windows.Forms.PrintDialog.Document%2A> property.</span></span> <span data-ttu-id="225aa-114">Dans l’exemple ci-dessous, aucun document d’impression n’est spécifié.</span><span class="sxs-lookup"><span data-stu-id="225aa-114">In the example below, no print document is specified.</span></span>  
  
     <span data-ttu-id="225aa-115">L’exemple suppose que votre formulaire contient un <xref:System.Windows.Forms.Button> (contrôle), un <xref:System.Drawing.Printing.PrintDocument> composant nommé `myDocument`et un <xref:System.Windows.Forms.PrintPreviewDialog> contrôle.</span><span class="sxs-lookup"><span data-stu-id="225aa-115">The example requires that your form has a <xref:System.Windows.Forms.Button> control, a <xref:System.Drawing.Printing.PrintDocument> component named `myDocument`, and a <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
       ByVal e As System.EventArgs) Handles Button1.Click  
       ' The print document 'myDocument' used below  
       ' is merely for an example.  
       ' You will have to specify your own print document.  
       PrintPreviewDialog1.Document = myDocument  
       PrintPreviewDialog1.ShowDialog()  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       // The print document 'myDocument' used below  
       // is merely for an example.  
       // You will have to specify your own print document.  
       printPreviewDialog1.Document = myDocument;  
       printPreviewDialog1.ShowDialog();  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          // The print document 'myDocument' used below  
          // is merely for an example.  
          // You will have to specify your own print document.  
          printPreviewDialog1->Document = myDocument;  
          printPreviewDialog1->ShowDialog();  
       }  
    ```  
  
     <span data-ttu-id="225aa-116">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Placez le code suivant dans le constructeur du formulaire pour inscrire le gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="225aa-116">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="225aa-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="225aa-117">See Also</span></span>  
 [<span data-ttu-id="225aa-118">Composant PrintDocument</span><span class="sxs-lookup"><span data-stu-id="225aa-118">PrintDocument Component</span></span>](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md)  
 [<span data-ttu-id="225aa-119">PrintPreviewDialog, contrôle</span><span class="sxs-lookup"><span data-stu-id="225aa-119">PrintPreviewDialog Control</span></span>](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)  
 [<span data-ttu-id="225aa-120">Prise en charge de l’impression dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="225aa-120">Windows Forms Print Support</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)  
 [<span data-ttu-id="225aa-121">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="225aa-121">Windows Forms</span></span>](../../../../docs/framework/winforms/index.md)
