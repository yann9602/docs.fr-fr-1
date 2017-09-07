---
title: Globalisation et localisation d'applications .NET Framework
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- international applications [.NET Framework]
- globalization [.NET Framework], encoding
- global applications
- internationalization
- world-ready applications
- application development [.NET Framework], globalization
- multilingual application development
ms.assetid: 9a59696b-d89b-45bd-946d-c75da4732d02
caps.latest.revision: 42
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 63832eb1b7c750bb4ef86660304ab883a7c3695f
ms.contentlocale: fr-fr
ms.lasthandoff: 09/05/2017

---
# <a name="globalizing-and-localizing-net-framework-applications"></a>Globalisation et localisation d'applications .NET Framework
Le développement d'une [application mondialisable](http://msdn.microsoft.com/goglobal/bb978433.aspx), notamment une application qui peut être localisée dans une ou plusieurs langues, implique trois étapes : la globalisation, l'examen de la faisabilité de localisation et la localisation.  
  
 [Globalisation](../../../docs/standard/globalization-localization/globalization.md)  
 Cette étape implique la conception et le codage d'une application indépendante des cultures et des langues qui prend en charge les interfaces utilisateur localisées et les paramètres régionaux pour tous les utilisateurs. Elle implique également de prendre des décisions relatives à la conception et à la programmation qui ne sont pas basées sur des hypothèses spécifiques à la culture. Même si une application globalisée n'est pas localisée, elle est néanmoins conçue et écrite pour pouvoir être ensuite localisée assez facilement en une ou plusieurs langues.  
  
 [Révision de l'adaptabilité](../../../docs/standard/globalization-localization/localizability-review.md)  
 Cette étape implique d’examiner le code et la conception d’une application pour vérifier qu’elle peut être localisée facilement et identifier les obstacles éventuels à la localisation, et de vérifier que le code exécutable de l’application est bien séparé de ses ressources. Si la phase de globalisation s'est déroulée correctement, l'examen de la faisabilité de localisation confirmera les choix de conception et de codage effectués pendant la globalisation. La phase d'examen de la faisabilité de localisation peut également identifier les problèmes restants afin de ne pas avoir à modifier le code source d'une application pendant la phase de localisation.  
  
 [Localisation](../../../docs/standard/globalization-localization/localization.md)  
 Cette étape implique la personnalisation d'une application pour des cultures ou des régions spécifiques. Si les étapes de globalisation et de faisabilité de localisation ont été effectuées correctement, la localisation consiste principalement à traduire l'interface utilisateur.  
  
 L'exécution de ces trois étapes offre deux avantages :  
  
-   Vous n'avez plus à adapter a posteriori une application conçue pour prendre en charge une seule culture, telle que l'anglais (États-Unis), pour prendre en charge d'autres cultures.  
  
-   Il en résulte des applications localisées plus stables qui présentent moins de bogues.  
  
 Le .NET Framework assure une prise en charge complète du développement d'applications mondialisables et localisées. En particulier, plusieurs membres de type de la bibliothèque de classes .NET Framework facilitent la globalisation en retournant des valeurs qui reflètent les conventions de la culture de l'utilisateur actuel ou d'une culture spécifiée. En outre, le .Net Framework prend en charge les assemblys satellites, qui simplifient le processus de localisation d'une application.  
  
 Pour obtenir des informations supplémentaires, consultez le [centre de développement sur la globalisation](http://go.microsoft.com/fwlink/?LinkId=235015).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Globalisation](../../../docs/standard/globalization-localization/globalization.md)  
 Décrit la première phase de création d'une application mondialisable, qui implique la conception et le codage d'une application indépendante des cultures et des langues.  
  
 [Révision de l'adaptabilité](../../../docs/standard/globalization-localization/localizability-review.md)  
 Décrit la seconde phase de création d'une application localisée, qui implique l'identification d'obstacles éventuels à la localisation.  
  
 [Localisation](../../../docs/standard/globalization-localization/localization.md)  
 Décrit la phase finale de la création d'une application localisée, qui implique la personnalisation de l'interface utilisateur d'une application en fonction de régions ou de cultures spécifiques.  
  
 [Opérations de chaînes indépendantes de la culture](../../../docs/standard/globalization-localization/culture-insensitive-string-operations.md)  
 Explique comment utiliser les méthodes et les classes .NET Framework dépendantes de la culture par défaut pour obtenir des résultats indépendants de la culture.  
  
 [Bonnes pratiques pour développer des applications mondialisables](../../../docs/standard/globalization-localization/best-practices-for-developing-world-ready-apps.md)  
 Décrit les meilleures pratiques en matière de globalisation, de localisation et de développement d'applications ASP.NET mondialisables.  
  
## <a name="reference"></a>Référence  
 Espace de noms <xref:System.Globalization?displayProperty=fullName>  
 Contient des classes qui définissent des informations liées à la culture, notamment la langue, le pays ou la région, les calendriers utilisés, les formats des dates, des monnaies et des nombres, ainsi que l'ordre de tri à respecter pour les chaînes.  
  
 Espace de noms <xref:System.Resources>  
 Fournit des classes pour créer, manipuler et utiliser des ressources.  
  
 Espace de noms <xref:System.Text>  
 Contient des classes représentant les encodages de caractères ASCII, ANSI, Unicode et autres.  
  
 [Resgen.exe (Resource File Generator)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md)  
 Explique comment utiliser Resgen.exe pour convertir des fichiers .txt et des fichiers .resx (format de ressource basé sur XML) en fichiers binaires .resources du Common Language Runtime.  
  
 [Winres.exe (éditeur de ressources Windows Forms)](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md)  
 Explique comment utiliser Winres.exe pour localiser des formulaires Windows Forms.

