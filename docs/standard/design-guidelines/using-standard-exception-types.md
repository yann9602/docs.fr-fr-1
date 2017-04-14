---
title: "&#192; l’aide des Types d’Exception Standard | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "lever des exceptions, les types standard"
  - "intercepter des exceptions"
  - "exceptions, intercepter"
  - "lever des exceptions"
ms.assetid: ab22ce03-78f9-4dca-8824-c7ed3bdccc27
caps.latest.revision: 17
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 17
---
# &#192; l’aide des Types d’Exception Standard
Cette section décrit les exceptions standard fournies par l’infrastructure et les détails de leur utilisation. La liste n’est pas exhaustive. Reportez\-vous à la documentation de référence du .NET Framework pour l’utilisation des autres types d’exception Framework.  
  
## Exception et SystemException  
 **X ne pas** lever <xref:System.Exception?displayProperty=fullName> ou <xref:System.SystemException?displayProperty=fullName>.  
  
 **X ne pas** catch `System.Exception` ou `System.SystemException` dans le code d’infrastructure, sauf si vous avez l’intention de lever à nouveau.  
  
 **X éviter** interception `System.Exception` ou `System.SystemException`, sauf dans les gestionnaires d’exceptions de niveau supérieur.  
  
## ApplicationException  
 **X ne pas** lever ou dériver de <xref:System.ApplicationException>.  
  
## InvalidOperationException  
 **✓ faire** lever un <xref:System.InvalidOperationException> Si l’objet est dans un état inapproprié.  
  
## ArgumentException, ArgumentNullException et ArgumentOutOfRangeException  
 **✓ faire** lever <xref:System.ArgumentException> ou l’un de ses sous\-types si des arguments incorrects sont passés à un membre. Préférez le type plus dérivé d’exception, le cas échéant.  
  
 **✓ faire** définir le `ParamName` propriété lors de la levée d’une des sous\-classes de `ArgumentException`.  
  
 Cette propriété représente le nom du paramètre ayant provoqué l’exception levée. Notez que la propriété peut être définie à l’aide d’une des surcharges de constructeur.  
  
 **✓ faire** utiliser `value` pour le nom du paramètre de valeur implicite des accesseurs Set de propriété.  
  
## NullReferenceException IndexOutOfRangeException et AccessViolationException  
 **X ne pas** autoriser API pouvant être appelées publiquement à lever explicitement ou implicitement <xref:System.NullReferenceException>, <xref:System.AccessViolationException>, ou <xref:System.IndexOutOfRangeException>. Ces exceptions sont réservées et levée par le moteur d’exécution et, dans que la plupart des cas indiquer un bogue.  
  
 Effectuer la vérification d’arguments pour éviter la levée de ces exceptions. Levée de ces exceptions expose des détails d’implémentation de votre méthode susceptibles d’être modifiées au fil du temps.  
  
## StackOverflowException  
 **X ne pas** lever explicitement <xref:System.StackOverflowException>. L’exception doit être levée explicitement uniquement par le CLR.  
  
 **X ne pas** catch `StackOverflowException`.  
  
 Il est quasiment impossible d’écrire du code managé qui reste cohérent en cas de dépassement arbitraire. Les parties du CLR non managées restent cohérentes pour déplacer les débordements de pile à des endroits bien définis à l’aide de sondes plutôt que par la régularisation de débordements de pile arbitraire.  
  
## OutOfMemoryException  
 **X ne pas** lever explicitement <xref:System.OutOfMemoryException>. Cette exception est levée uniquement par l’infrastructure du CLR.  
  
## ComException et SEHException ExecutionEngineException  
 **X ne pas** lever explicitement <xref:System.Runtime.InteropServices.COMException>,  <xref:System.ExecutionEngineException>, et <xref:System.Runtime.InteropServices.SEHException>. Ces exceptions doivent être levées uniquement par l’infrastructure du CLR.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimé avec l’autorisation de Pearson éducation, Inc. à partir de [Framework Design Guidelines : Conventions, langages et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison\-Wesley Professional dans le cadre de la série de développement de Microsoft Windows.*  
  
## Voir aussi  
 [Instructions de conception d’infrastructure](../../../docs/standard/design-guidelines/index.md)   
 [Instructions de conception pour les Exceptions](../../../docs/standard/design-guidelines/exceptions.md)