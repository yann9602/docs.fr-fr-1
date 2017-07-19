---
title: "Comment&#160;: simuler des &#233;v&#233;nements de la souris et du clavier dans le code | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "claviers, simulation d’événement"
  - "entrée d’utilisateur, simulation"
  - "SendKeys, utilisation"
  - "clics de souris, simulation"
  - "souris, simulation d’événement"
ms.assetid: 6abcb67e-3766-4af2-9590-bf5dabd17e41
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Comment&#160;: simuler des &#233;v&#233;nements de la souris et du clavier dans le code
Windows Forms fournit plusieurs options pour simuler par programmation l'entrée de souris et de clavier. Cette rubrique offre une vue d'ensemble de ces options.  
  
## Simulation de l'entrée de souris  
 Le meilleur moyen de simuler des événements de souris consiste à appeler la méthode `On`*EventName* qui déclenche l'événement de souris que vous souhaitez simuler. Cette option est généralement possible uniquement dans les contrôles et les formulaires personnalisés, car les méthodes qui déclenchent des événements sont protégées et ne sont pas accessibles en dehors du contrôle ou du formulaire. Par exemple, les étapes suivantes illustrent comment simuler un clic sur le bouton droit de la souris dans le code.  
  
#### Pour cliquer sur le bouton droit de la souris par programmation  
  
1.  Créez un <xref:System.Windows.Forms.MouseEventArgs> dont la propriété <xref:System.Windows.Forms.MouseEventArgs.Button%2A> a la valeur <xref:System.Windows.Forms.MouseButtons?displayProperty=fullName>.  
  
2.  Appelez la méthode <xref:System.Windows.Forms.Control.OnMouseClick%2A> avec ce <xref:System.Windows.Forms.MouseEventArgs> comme argument.  
  
 Pour plus d’informations sur les contrôles personnalisés, consultez [Développement de contrôles Windows Forms au moment du design](../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md).  
  
 Il existe d'autres manières de simuler l'entrée de souris. Par exemple, vous pouvez définir par programmation une propriété de contrôle qui représente un état qui est généralement défini par une entrée de souris \(telle que la propriété <xref:System.Windows.Forms.CheckBox.Checked%2A> du contrôle <xref:System.Windows.Forms.CheckBox>\) ou vous pouvez appeler directement le délégué qui est attaché à l'événement que vous souhaitez simuler.  
  
## Simulation de l'entrée au clavier  
 Bien que vous puissiez simuler l'entrée au clavier à l'aide des stratégies abordées ci\-dessus pour l'entrée de souris, Windows Forms fournit également la classe <xref:System.Windows.Forms.SendKeys> pour envoyer des séquences de touches à l'application active.  
  
> [!CAUTION]
>  Si votre application est prévue pour une utilisation internationale avec différents claviers, l'utilisation de <xref:System.Windows.Forms.SendKeys.Send%2A?displayProperty=fullName> peut produire des résultats imprévisibles et doit être évitée.  
  
> [!NOTE]
>  La classe <xref:System.Windows.Forms.SendKeys> a été mise à jour pour .NET Framework 3.0 pour pouvoir être utilisée dans les applications qui s'exécutent sur Windows Vista. La sécurité renforcée de Windows Vista \(également appelée Contrôle de compte d'utilisateur\) empêche le fonctionnement correcte de l'implémentation précédente.  
>   
>  La classe <xref:System.Windows.Forms.SendKeys> est vulnérable aux problèmes de synchronisation, que certains développeurs ont dû contourner. L'implémentation mise à jour est toujours vulnérable aux problèmes de synchronisation, mais est légèrement plus rapide et peut nécessiter certaines modifications des solutions de contournement. La classe <xref:System.Windows.Forms.SendKeys> tente d'abord d'utiliser l'implémentation précédente et, en cas d'échec, utilise la nouvelle implémentation. Ainsi, la classe <xref:System.Windows.Forms.SendKeys> peut se comporter différemment sur différents systèmes d'exploitation. En outre, quand la classe <xref:System.Windows.Forms.SendKeys> utilise la nouvelle implémentation, la méthode <xref:System.Windows.Forms.SendKeys.SendWait%2A> n'attend pas que les messages soient traités quand ils sont envoyés à un autre processus.  
>   
>  Si votre application repose sur un comportement cohérent indépendamment du système d'exploitation, vous pouvez forcer la classe <xref:System.Windows.Forms.SendKeys> à utiliser la nouvelle implémentation en ajoutant le paramètre d'application suivant à votre fichier app.config.  
>   
>  `<appSettings>`  
>   
>  `<add key="SendKeys" value="SendInput"/>`  
>   
>  `</appSettings>`  
>   
>  Pour forcer la classe <xref:System.Windows.Forms.SendKeys> à utiliser l'implémentation précédente, utilisez plutôt la valeur `"JournalHook"`.  
  
#### Pour envoyer une séquence de touches à la même application  
  
1.  Appelez la méthode <xref:System.Windows.Forms.SendKeys.Send%2A> ou <xref:System.Windows.Forms.SendKeys.SendWait%2A> de la classe <xref:System.Windows.Forms.SendKeys>. Les séquences de touches spécifiées seront reçues par le contrôle actif de l'application. L'exemple de code suivant utilise <xref:System.Windows.Forms.SendKeys.Send%2A> pour simuler une pression sur la touche Entrée quand l'utilisateur double\-clique sur la surface du formulaire. Cet exemple suppose que l'on a un <xref:System.Windows.Forms.Form> avec un seul contrôle <xref:System.Windows.Forms.Button> ayant un index de tabulation de 0.  
  
     [!code-cpp[System.Windows.Forms.SimulateKeyPress#10](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/cpp/form1.cpp#10)]
     [!code-csharp[System.Windows.Forms.SimulateKeyPress#10](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/CS/form1.cs#10)]
     [!code-vb[System.Windows.Forms.SimulateKeyPress#10](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/VB/form1.vb#10)]  
  
#### Pour envoyer une séquence de touches vers une autre application  
  
1.  Activez la fenêtre d'application qui recevra les séquences de touches, puis appelez la méthode <xref:System.Windows.Forms.SendKeys.Send%2A> ou <xref:System.Windows.Forms.SendKeys.SendWait%2A>. Comme il n'existe aucune méthode managée permettant d'activer une autre application, vous devez utiliser des méthodes Windows natives pour forcer le focus sur d'autres applications. L'exemple de code suivant utilise l'appel de code non managé pour appeler les méthodes `FindWindow` et `SetForegroundWindow` pour activer la fenêtre de l'application Calculatrice, puis appelle <xref:System.Windows.Forms.SendKeys.SendWait%2A> pour émettre une série de calculs vers l'application Calculatrice.  
  
    > [!NOTE]
    >  Les paramètres corrects de l'appel `FindWindow` qui recherche l'application Calculatrice varient en fonction de votre version de Windows.  Le code suivant recherche l'application Calculatrice sur [!INCLUDE[win7](../../../includes/win7-md.md)]. Sur [!INCLUDE[windowsver](../../../includes/windowsver-md.md)], remplacez le premier paramètre par « SciCalc ». Vous pouvez utiliser l'outil Spy\+\+, fourni avec Visual Studio, pour déterminer les paramètres corrects.  
  
     [!code-cpp[System.Windows.Forms.SimulateKeyPress#5](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/cpp/form1.cpp#5)]
     [!code-csharp[System.Windows.Forms.SimulateKeyPress#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/CS/form1.cs#5)]
     [!code-vb[System.Windows.Forms.SimulateKeyPress#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/VB/form1.vb#5)]  
  
## Exemple  
 L'exemple de code suivant est l'application complète pour les exemples de code précédents.  
  
 [!code-cpp[System.Windows.Forms.SimulateKeyPress#0](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/cpp/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.SimulateKeyPress#0](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.SimulateKeyPress#0](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/VB/form1.vb#0)]  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   des références aux assemblys System, System.Drawing et System.Windows.Forms.  
  
 Pour plus d’informations sur la création de cet exemple à partir de la ligne de commande associée à [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] ou à [!INCLUDE[csprcs](../../../includes/csprcs-md.md)], consultez les pages [Génération à partir de la ligne de commande](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md) ou [Génération à partir de la ligne de commande avec csc.exe](../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Vous pouvez également générer cet exemple dans [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] en collant le code dans un nouveau projet.  Consultez également la page [Comment : compiler et exécuter un exemple complet de code Windows Forms à l’aide de Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## Voir aussi  
 [Entrées d'utilisateur dans les Windows Forms](../../../docs/framework/winforms/user-input-in-windows-forms.md)