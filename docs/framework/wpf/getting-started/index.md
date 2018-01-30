---
title: "Bien démarrer (WPF)"
ms.custom: 
ms.date: 01/26/2018
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- getting started [WPF]
- introduction [WPF]
- WPF [WPF], getting started
ms.assetid: 04f91da8-708c-46c7-8172-f1695ec847cd
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: eded6de5de269e7b49a87da31590267a5350f161
ms.sourcegitcommit: f28752eab00d2bd97e971542c0f49ce63cfbc239
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2018
---
# <a name="getting-started-wpf"></a><span data-ttu-id="28fe0-102">Bien démarrer (WPF)</span><span class="sxs-lookup"><span data-stu-id="28fe0-102">Getting Started (WPF)</span></span>
<span data-ttu-id="28fe0-103">Windows Presentation Foundation (WPF) est un framework d’interface utilisateur qui permet de créer des applications de bureau clientes.</span><span class="sxs-lookup"><span data-stu-id="28fe0-103">Windows Presentation Foundation (WPF) is a UI framework that creates desktop client applications.</span></span> <span data-ttu-id="28fe0-104">La plateforme de développement WPF prend en charge un large éventail de fonctionnalités de développement d’applications, notamment un modèle d’application, des ressources, des contrôles, des graphiques, une disposition, la liaison de données, des documents et la sécurité.</span><span class="sxs-lookup"><span data-stu-id="28fe0-104">The WPF development platform supports a broad set of application development features, including an application model, resources, controls, graphics, layout, data binding, documents, and security.</span></span> <span data-ttu-id="28fe0-105">S’agissant d’un sous-ensemble du .NET Framework, si vous avez déjà créé des applications avec le .NET Framework à l’aide d’ASP.NET ou de Windows Forms, l’environnement de programmation doit vous être familier.</span><span class="sxs-lookup"><span data-stu-id="28fe0-105">It is a subset of the .NET Framework, so if you have previously built applications with the .NET Framework using ASP.NET or Windows Forms, the programming experience should be familiar.</span></span> <span data-ttu-id="28fe0-106">WPF utilise le langage XAML (Extensible Application Markup Language) pour fournir un modèle déclaratif à des fins de programmation d’applications.</span><span class="sxs-lookup"><span data-stu-id="28fe0-106">WPF uses the Extensible Application Markup Language (XAML) to provide a declarative model for application programming.</span></span> <span data-ttu-id="28fe0-107">Cette section contient des rubriques de présentation et d’aide à la prise en main de WPF.</span><span class="sxs-lookup"><span data-stu-id="28fe0-107">This section has topics that introduce and help you get started with WPF.</span></span>  
  
## <a name="where-should-i-start"></a><span data-ttu-id="28fe0-108">Où est-ce que je dois démarrer ?</span><span class="sxs-lookup"><span data-stu-id="28fe0-108">Where Should I Start?</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="28fe0-109">Je veux rentrer dans le vif du sujet...</span><span class="sxs-lookup"><span data-stu-id="28fe0-109">I want to jump right in…</span></span>|[<span data-ttu-id="28fe0-110">Procédure pas à pas : ma première application de bureau WPF</span><span class="sxs-lookup"><span data-stu-id="28fe0-110">Walkthrough: My first WPF desktop application</span></span>](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)|  
|<span data-ttu-id="28fe0-111">Comment concevoir l’interface utilisateur de l’application ?</span><span class="sxs-lookup"><span data-stu-id="28fe0-111">How do I design the application UI?</span></span>|[<span data-ttu-id="28fe0-112">Conception XAML dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="28fe0-112">Designing XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)|  
|<span data-ttu-id="28fe0-113">Vous débutez avec .NET ?</span><span class="sxs-lookup"><span data-stu-id="28fe0-113">New to .NET?</span></span>|<span data-ttu-id="28fe0-114">[Vue d’ensemble du .NET Framework](https://msdn.microsoft.com/library/zw4w595w\(v=vs.140\).aspx)</span><span class="sxs-lookup"><span data-stu-id="28fe0-114">[Overview of the .NET Framework](https://msdn.microsoft.com/library/zw4w595w\(v=vs.140\).aspx)</span></span><br /><br /> [<span data-ttu-id="28fe0-115">Éléments de base des applications .NET Framework</span><span class="sxs-lookup"><span data-stu-id="28fe0-115">.NET Framework Application Essentials</span></span>](../../../../docs/standard/application-essentials.md)<br /><br /> <span data-ttu-id="28fe0-116">[Bien démarrer avec Visual Basic et Visual C#](https://msdn.microsoft.com/library/dd492171\(v=vs.140\).aspx)</span><span class="sxs-lookup"><span data-stu-id="28fe0-116">[Getting Started with Visual C# and Visual Basic](https://msdn.microsoft.com/library/dd492171\(v=vs.140\).aspx)</span></span>|  
|<span data-ttu-id="28fe0-117">En savoir plus sur WPF...</span><span class="sxs-lookup"><span data-stu-id="28fe0-117">Tell me more about WPF…</span></span>|[<span data-ttu-id="28fe0-118">Présentation de WPF dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="28fe0-118">Introduction to WPF in Visual Studio</span></span>](../../../../docs/framework/wpf/getting-started/introduction-to-wpf-in-vs.md)<br /><br /> [<span data-ttu-id="28fe0-119">Vue d’ensemble du langage XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="28fe0-119">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)<br /><br /> [<span data-ttu-id="28fe0-120">Contrôles</span><span class="sxs-lookup"><span data-stu-id="28fe0-120">Controls</span></span>](../../../../docs/framework/wpf/controls/index.md)<br /><br /> [<span data-ttu-id="28fe0-121">Vue d’ensemble de la liaison de données</span><span class="sxs-lookup"><span data-stu-id="28fe0-121">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)|  
|<span data-ttu-id="28fe0-122">Vous êtes développeur Windows Forms ?</span><span class="sxs-lookup"><span data-stu-id="28fe0-122">Are you a Windows Forms developer?</span></span>|[<span data-ttu-id="28fe0-123">Contrôles Windows Forms et contrôles WPF équivalents</span><span class="sxs-lookup"><span data-stu-id="28fe0-123">Windows Forms Controls and Equivalent WPF Controls</span></span>](../../../../docs/framework/wpf/advanced/windows-forms-controls-and-equivalent-wpf-controls.md)<br /><br /> [<span data-ttu-id="28fe0-124">Interopérabilité WPF et Windows Forms</span><span class="sxs-lookup"><span data-stu-id="28fe0-124">WPF and Windows Forms Interoperation</span></span>](../../../../docs/framework/wpf/advanced/wpf-and-windows-forms-interoperation.md)|  
  
## <a name="see-also"></a><span data-ttu-id="28fe0-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="28fe0-125">See Also</span></span>  
 [<span data-ttu-id="28fe0-126">Bibliothèque de classes</span><span class="sxs-lookup"><span data-stu-id="28fe0-126">Class Library</span></span>](../../../../docs/framework/wpf/class-library-wpf.md)  
 [<span data-ttu-id="28fe0-127">Développement de l’application</span><span class="sxs-lookup"><span data-stu-id="28fe0-127">Application Development</span></span>](../../../../docs/framework/wpf/app-development/index.md)  
 [<span data-ttu-id="28fe0-128">Centre de développement .NET Framework</span><span class="sxs-lookup"><span data-stu-id="28fe0-128">.NET Framework Developer Center</span></span>](https://www.microsoft.com/net)
