---
title: "Considérations sur l'hébergement d'un contrôle ActiveX dans un Windows Form"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms controls, ActiveX controls
- ActiveX controls [Windows Forms], hosting
- Windows Forms, ActiveX controls
- Windows Forms, hosting ActiveX controls
- ActiveX controls [Windows Forms], adding
ms.assetid: 2509302d-a74e-484f-9890-2acdbfa67a68
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 23c8476e4013cca6d906d85f11658deddc585869
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="considerations-when-hosting-an-activex-control-on-a-windows-form"></a><span data-ttu-id="a256a-102">Considérations sur l'hébergement d'un contrôle ActiveX dans un Windows Form</span><span class="sxs-lookup"><span data-stu-id="a256a-102">Considerations When Hosting an ActiveX Control on a Windows Form</span></span>
<span data-ttu-id="a256a-103">Bien que les Windows Forms aient été optimisés pour héberger des contrôles Windows Forms, vous pouvez néanmoins utiliser des contrôles ActiveX.</span><span class="sxs-lookup"><span data-stu-id="a256a-103">Although Windows Forms have been optimized to host Windows Forms controls, you can still use ActiveX controls.</span></span> <span data-ttu-id="a256a-104">Gardez à l’esprit les considérations suivantes lors de la planification d’une application qui utilise des contrôles ActiveX :</span><span class="sxs-lookup"><span data-stu-id="a256a-104">Keep the following considerations in mind when planning an application that uses ActiveX controls:</span></span>  
  
-   <span data-ttu-id="a256a-105">**Sécurité** : le common language runtime a été amélioré en ce qui concerne la sécurité d’accès du code.</span><span class="sxs-lookup"><span data-stu-id="a256a-105">**Security** The common language runtime has been enhanced with regard to code access security.</span></span> <span data-ttu-id="a256a-106">Les applications recourant aux Windows Forms peuvent fonctionner sans problème dans un environnement totalement fiable et dans un environnement partiellement fiable avec la plupart des fonctionnalités disponibles.</span><span class="sxs-lookup"><span data-stu-id="a256a-106">Applications featuring Windows Forms can run in a fully trusted environment without issue and in a semi-trusted environment with most of the functionality accessible.</span></span> <span data-ttu-id="a256a-107">Les contrôles Windows Forms peuvent être hébergés dans un navigateur sans aucune complication.</span><span class="sxs-lookup"><span data-stu-id="a256a-107">Windows Forms controls can be hosted in a browser with no complications.</span></span> <span data-ttu-id="a256a-108">Cependant, les contrôles ActiveX dans les Windows Forms ne tirent pas parti de ces améliorations de sécurité.</span><span class="sxs-lookup"><span data-stu-id="a256a-108">However, ActiveX controls on Windows Forms cannot take advantage of these security enhancements.</span></span> <span data-ttu-id="a256a-109">Exécution d’un contrôle ActiveX nécessite une autorisation de code non managé, qui est définie avec la <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A?displayProperty=nameWithType> propriété.</span><span class="sxs-lookup"><span data-stu-id="a256a-109">Running an ActiveX control requires unmanaged code permission, which is set with the <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="a256a-110">Pour plus d’informations sur la sécurité et l’autorisation de code non managé, consultez <xref:System.Security.Permissions.SecurityPermissionAttribute>.</span><span class="sxs-lookup"><span data-stu-id="a256a-110">For more information about security and unmanaged code permission, see <xref:System.Security.Permissions.SecurityPermissionAttribute>.</span></span>  
  
-   <span data-ttu-id="a256a-111">**Coût total de possession** : les contrôles ActiveX ajoutés à un Windows Form sont déployés dans leur intégralité avec ce Windows Form, ce qui peut accroître considérablement la taille des fichiers créés.</span><span class="sxs-lookup"><span data-stu-id="a256a-111">**Total Cost of Ownership** ActiveX controls added to a Windows Form are deployed with that Windows Form in their entirety, which can add significantly to the size of the file(s) created.</span></span> <span data-ttu-id="a256a-112">En outre, l’utilisation de contrôles ActiveX sur des Windows Forms nécessite l’écriture dans le Registre.</span><span class="sxs-lookup"><span data-stu-id="a256a-112">Additionally, using ActiveX controls on Windows Forms requires writing to the registry.</span></span> <span data-ttu-id="a256a-113">Ceci est plus invasif sur l’ordinateur d’un utilisateur que les contrôles Windows Forms, qui ne le nécessitent pas.</span><span class="sxs-lookup"><span data-stu-id="a256a-113">This is more invasive to a user's computer than Windows Forms controls, which do not require this.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a256a-114">L’utilisation d’un contrôle ActiveX nécessite l’utilisation d’un wrapper COM interop.</span><span class="sxs-lookup"><span data-stu-id="a256a-114">Working with an ActiveX control requires the use of a COM interop wrapper.</span></span> <span data-ttu-id="a256a-115">Pour plus d’informations, consultez [Interopérabilité COM en Visual Basic et Visual C#](~/docs/visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="a256a-115">For more information, see [COM Interoperability in Visual Basic and Visual C#](~/docs/visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a256a-116">Si le nom d’un membre du contrôle ActiveX correspond à un nom défini dans le [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], l’importateur de contrôles ActiveX fera précéder le nom du membre avec **Ctl** lorsqu’il crée le <xref:System.Windows.Forms.AxHost> classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="a256a-116">If the name of a member of the ActiveX control matches a name defined in the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], then the ActiveX Control Importer will prefix the member name with **Ctl** when it creates the <xref:System.Windows.Forms.AxHost> derived class.</span></span> <span data-ttu-id="a256a-117">Par exemple, si votre contrôle ActiveX a un membre nommé **Layout**, il est renommé **CtlLayout** dans la classe dérivée de AxHost, car l’événement **Layout** est défini dans le [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a256a-117">For example, if your ActiveX control has a member named **Layout**, it is renamed **CtlLayout** in the AxHost-derived class because the **Layout** event is defined within the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a256a-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a256a-118">See Also</span></span>  
 [<span data-ttu-id="a256a-119">Guide pratique pour ajouter des contrôles ActiveX aux Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a256a-119">How to: Add ActiveX Controls to Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-add-activex-controls-to-windows-forms.md)  
 [<span data-ttu-id="a256a-120">Sécurité d’accès du code</span><span class="sxs-lookup"><span data-stu-id="a256a-120">Code Access Security</span></span>](../../../../docs/framework/misc/code-access-security.md)  
 [<span data-ttu-id="a256a-121">Comparaison des contrôles et des objets programmables dans divers langages et bibliothèques</span><span class="sxs-lookup"><span data-stu-id="a256a-121">Controls and Programmable Objects Compared in Various Languages and Libraries</span></span>](http://msdn.microsoft.com/library/021f2a1b-8247-4348-a5ad-e1d9ab23004b)  
 [<span data-ttu-id="a256a-122">Placement de contrôles dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a256a-122">Putting Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/putting-controls-on-windows-forms.md)  
 [<span data-ttu-id="a256a-123">Contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a256a-123">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)
