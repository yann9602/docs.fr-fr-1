---
title: "UI Automation d&#39;un contr&#244;le personnalis&#233; WPF | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "contrôles personnalisés (WPF), appliquer UI automation"
  - "accessibilité (WPF), appliquer à des contrôles personnalisés"
  - "contrôles personnalisés (WPF), améliorer l’accessibilité"
  - "Automation d’interface utilisateur (WPF), avec des contrôles personnalisés"
ms.assetid: 47b310fc-fbd5-4ce2-a606-22d04c6d4911
caps.latest.revision: 34
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 34
---
# UI Automation d&#39;un contr&#244;le personnalis&#233; WPF
[!INCLUDE[TLA#tla_uiautomation](../../../../includes/tlasharptla-uiautomation-md.md)]Fournit une interface unique et généralisée que les clients peuvent utiliser pour examiner ou faire fonctionner les interfaces utilisateur de diverses plateformes et infrastructures automation. [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]Active le code d’assurance qualité (test) et les applications d’accessibilité telles que les lecteurs d’écran pour examiner les éléments d’interface utilisateur et de simuler l’interaction utilisateur avec eux à partir de tout autre code. Pour plus d’informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] sur toutes les plateformes, consultez la rubrique d’accessibilité.  
  
 Cette rubrique décrit comment implémenter un fournisseur d’UI Automation côté serveur pour un contrôle personnalisé qui s’exécute dans une application WPF. WPF prend en charge [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] à travers une arborescence d’objets homologues automation en parallèle à l’arborescence d’éléments d’interface utilisateur. Code de test et les applications qui fournissent des fonctionnalités d’accessibilité peuvent utiliser des objets homologues automation directement (pour le code in-process) ou à travers l’interface généralisée fournie par [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)].  
  
 
  
<a name="AutomationPeerClasses"></a>   
## <a name="automation-peer-classes"></a>Classes homologues Automation  
 Prise en charge des contrôles WPF [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] à travers une arborescence de classes homologues qui dérivent de <xref:System.Windows.Automation.Peers.AutomationPeer>. Par convention, les noms de classes homologues commencent par le nom de classe de contrôle et se terminent par « AutomationPeer ». Par exemple, <xref:System.Windows.Automation.Peers.ButtonAutomationPeer> est la classe homologue pour la <xref:System.Windows.Controls.Button> classe de contrôle. Les classes homologues sont à peu près équivalents à [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] types de contrôles, mais sont spécifiques à [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] éléments. Code d’Automation qui accède aux applications WPF à travers le [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] interface n’utilise pas directement les homologues automation, mais le code d’automation dans le même espace de processus peut utiliser directement les homologues automation.  
  
<a name="BuiltInAutomationPeerClasses"></a>   
## <a name="built-in-automation-peer-classes"></a>Classes homologues Automation intégrées  
 Éléments implémentent une classe homologue automation s’ils acceptent l’activité de l’interface de l’utilisateur, ou s’ils contiennent des informations requises par les utilisateurs d’applications de lecteur d’écran. Pas tous les éléments visuels WPF ont des homologues automation. Exemples de classes qui implémentent des homologues automation sont <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.TextBox>, et <xref:System.Windows.Controls.Label>. Exemples de classes qui n’implémentent pas d’homologues automation sont des classes qui dérivent de <xref:System.Windows.Controls.Decorator>, tel que <xref:System.Windows.Controls.Border>et des classes basées sur <xref:System.Windows.Controls.Panel>, tel que <xref:System.Windows.Controls.Grid> et <xref:System.Windows.Controls.Canvas>.  
  
 La base de <xref:System.Windows.Controls.Control> classe n’a pas de classe homologue correspondante. Si vous avez besoin d’une classe homologue pour correspondre à un contrôle personnalisé qui dérive de <xref:System.Windows.Controls.Control>, vous devez dériver la classe homologue personnalisée de <xref:System.Windows.Automation.Peers.FrameworkElementAutomationPeer>.  
  
<a name="SecurityConsiderations"></a>   
## <a name="security-considerations-for-derived-peers"></a>Considérations sur la sécurité des homologues dérivés  
 Les homologues Automation doivent s’exécuter dans un environnement de confiance partielle. Code de l’assembly UIAutomationClient n’est pas configuré pour s’exécuter dans un environnement de confiance partielle et code homologue automation ne doit pas référencer cet assembly. Au lieu de cela, vous devez utiliser les classes de l’assembly UIAutomationTypes. Par exemple, vous devez utiliser le <xref:System.Windows.Automation.AutomationElementIdentifiers> classe à partir de l’assembly UIAutomationTypes, qui correspond à la <xref:System.Windows.Automation.AutomationElement> classe de l’assembly UIAutomationClient. Il est possible de référencer l’assembly UIAutomationTypes dans le code homologue automation.  
  
<a name="PeerNavigation"></a>   
## <a name="peer-navigation"></a>Navigation homologue  
 Après avoir localisé un homologue automation, code in-process peut naviguer l’arborescence homologue en appelant l’objet <xref:System.Windows.Automation.Peers.AutomationPeer.GetChildren%2A> et <xref:System.Windows.Automation.Peers.AutomationPeer.GetParent%2A> méthodes. Navigation parmi les [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] éléments au sein d’un contrôle est pris en charge par l’implémentation de l’homologue de la <xref:System.Windows.Automation.Peers.AutomationPeer.GetChildrenCore%2A> (méthode). Le système UI Automation appelle cette méthode pour générer une arborescence de sous-éléments contenus dans un contrôle ; par exemple, les éléments de liste dans une zone de liste. La valeur par défaut <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetChildrenCore%2A?displayProperty=fullName> méthode parcourt l’arborescence visuelle d’éléments pour générer l’arborescence d’homologues automation. Contrôles personnalisés substituer cette méthode pour exposer des éléments enfants aux clients automation, en retournant les homologues automation des éléments qui acheminent des informations ou permettent l’interaction avec l’utilisateur.  
  
<a name="Customizations"></a>   
## <a name="customizations-in-a-derived-peer"></a>Personnalisations dans un homologue dérivé  
 Toutes les classes qui dérivent de <xref:System.Windows.UIElement> et <xref:System.Windows.ContentElement> contiennent la méthode virtuelle protégée <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A>. WPF appelle <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> pour obtenir l’objet homologue automation pour chaque contrôle. Code d’Automation peut utiliser l’homologue pour obtenir des informations sur les caractéristiques et les fonctionnalités d’un contrôle et pour simuler une utilisation interactive. Un contrôle personnalisé qui prend en charge automation doit substituer <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> et retourner une instance d’une classe qui dérive de <xref:System.Windows.Automation.Peers.AutomationPeer>. Par exemple, si un contrôle personnalisé dérive la <xref:System.Windows.Controls.Primitives.ButtonBase> (classe), puis l’objet retourné par <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> doit dériver de <xref:System.Windows.Automation.Peers.ButtonBaseAutomationPeer>.  
  
 Lorsque vous implémentez un contrôle personnalisé, vous devez substituer les méthodes « Core » à partir de la classe homologue automation de base qui décrivent le comportement unique et spécifique à votre contrôle personnalisé.  
  
### <a name="override-oncreateautomationpeer"></a>Substituer OnCreateAutomationPeer  
 Remplacer la <xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> méthode pour votre contrôle personnalisé afin qu’il retourne votre objet fournisseur, qui doit dériver directement ou indirectement de <xref:System.Windows.Automation.Peers.AutomationPeer>.  
  
### <a name="override-getpattern"></a>Substituer GetPattern  
 Homologues Automation simplifient quelques aspects d’implémentation de côté serveur [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] fournisseurs, mais les homologues automation de contrôle personnalisés doivent encore gérer des interfaces de modèle. Comme les fournisseurs non WPF, homologues prennent en charge les modèles de contrôle en fournissant des implémentations d’interfaces dans le <xref:System.Windows.Automation.Provider?displayProperty=fullName> espace de noms, tel que <xref:System.Windows.Automation.Provider.IInvokeProvider>. Les interfaces de modèle de contrôle peuvent être implémentées par l’homologue lui-même ou par un autre objet. Implémentation de l’homologue de <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> retourne l’objet qui prend en charge le modèle spécifié. [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]code appelle la <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> (méthode) et spécifie un <xref:System.Windows.Automation.Peers.PatternInterface> valeur d’énumération. La substitution de <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> doit retourner l’objet qui implémente le modèle spécifié. Si votre contrôle ne possède pas une implémentation personnalisée d’un modèle, vous pouvez appeler implémentation du type de base de <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> pour récupérer son implémentation ou null si le modèle n’est pas pris en charge pour ce type de contrôle. Par exemple, un contrôle NumericUpDown personnalisé peut être défini sur une valeur dans une plage, donc ses [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] homologue implémente la <xref:System.Windows.Automation.Provider.IRangeValueProvider> interface. L’exemple suivant montre comment de l’homologue <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> méthode est substituée pour répondre à une <xref:System.Windows.Automation.Peers.PatternInterface?displayProperty=fullName> valeur.  
  
 [!code-csharp[CustomControlNumericUpDown#GetPattern](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#getpattern)]
 [!code-vb[CustomControlNumericUpDown#GetPattern](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#getpattern)]  
  
 A <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A> méthode peut également spécifier un sous-élément comme fournisseur de modèles. Le code suivant montre comment <xref:System.Windows.Controls.ItemsControl> transfère la gestion du modèle à l’homologue de ses propres défilement <xref:System.Windows.Controls.ScrollViewer> contrôle.  
  
```csharp  
public override object GetPattern(PatternInterface patternInterface)  
{  
    if (patternInterface == PatternInterface.Scroll)  
    {  
        ItemsControl owner = (ItemsControl) base.Owner;  
  
        // ScrollHost is internal to the ItemsControl class  
        if (owner.ScrollHost != null)  
        {  
            AutomationPeer peer = UIElementAutomationPeer.CreatePeerForElement(owner.ScrollHost);  
            if ((peer != null) && (peer is IScrollProvider))  
            {  
                peer.EventsSource = this;  
                return (IScrollProvider) peer;  
            }  
        }  
    }  
    return base.GetPattern(patternInterface);  
}  
```  
  
```vb  
Public Class Class1  
    Public Overrides Function GetPattern(ByVal patternInterface__1 As PatternInterface) As Object  
        If patternInterface1 = PatternInterface.Scroll Then  
            Dim owner As ItemsControl = DirectCast(MyBase.Owner, ItemsControl)  
  
            ' ScrollHost is internal to the ItemsControl class  
            If owner.ScrollHost IsNot Nothing Then  
                Dim peer As AutomationPeer = UIElementAutomationPeer.CreatePeerForElement(owner.ScrollHost)  
                If (peer IsNot Nothing) AndAlso (TypeOf peer Is IScrollProvider) Then  
                    peer.EventsSource = Me  
                    Return DirectCast(peer, IScrollProvider)  
                End If  
            End If  
        End If  
        Return MyBase.GetPattern(patternInterface1)  
    End Function  
End Class  
```  
  
 Pour spécifier un sous-élément de la gestion du modèle, ce code obtient l’objet de sous-élément, crée un homologue en utilisant la <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.CreatePeerForElement%2A> (méthode), définit le <xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A> propriété du nouvel homologue à l’homologue actuel et retourne le nouvel homologue. Paramètre <xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A> à un sous-élément empêche le sous-élément d’apparaître dans l’arborescence homologue automation et désigne tous les événements déclenchés par le sous-élément comme étant originaire du contrôle spécifié dans <xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A>. Le <xref:System.Windows.Controls.ScrollViewer> contrôle n’apparaît pas dans l’arborescence automation et les événements de défilement qu’il génère semblent provenir du <xref:System.Windows.Controls.ItemsControl> objet.  
  
### <a name="override-core-methods"></a>Substituez les méthodes « Core »  
 Code d’Automation obtient des informations sur votre contrôle en appelant des méthodes publiques de la classe homologue. Pour fournir des informations sur votre contrôle, substituez chaque méthode dont le nom se termine par « Core » lorsque votre implémentation de contrôle diffère de celle fournie par la classe homologue automation de base. Au minimum, votre contrôle doit implémenter le <xref:System.Windows.Automation.Peers.AutomationPeer.GetClassNameCore%2A> et <xref:System.Windows.Automation.Peers.AutomationPeer.GetAutomationControlTypeCore%2A> méthodes, comme indiqué dans l’exemple suivant.  
  
 [!code-csharp[CustomControlNumericUpDown#CoreOverrides](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#coreoverrides)]
 [!code-vb[CustomControlNumericUpDown#CoreOverrides](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#coreoverrides)]  
  
 Votre implémentation de <xref:System.Windows.Automation.Peers.AutomationPeer.GetAutomationControlTypeCore%2A> décrit votre contrôle en retournant un <xref:System.Windows.Automation.ControlType> valeur. Bien que vous pouvez retourner <xref:System.Windows.Automation.ControlType.Custom?displayProperty=fullName>, vous devez retourner un des types de contrôle plus spécifiques s’il décrit votre contrôle correctement. Une valeur de retour de <xref:System.Windows.Automation.ControlType.Custom?displayProperty=fullName> nécessite un travail supplémentaire pour implémenter le fournisseur de [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)], et [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] produits clients ne peuvent pas anticiper la structure de contrôle, l’interaction du clavier et des modèles de contrôle possibles.  
  
 Implémentez la <xref:System.Windows.Automation.Peers.AutomationPeer.IsContentElementCore%2A> et <xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A> méthodes pour indiquer si votre contrôle contient des données ou s’il accomplit un rôle interactif dans l’interface utilisateur (ou les deux). Par défaut, ces deux méthodes retournent `true`. Ces paramètres facilitent l’utilisation des outils d’automatisation telles que les lecteurs d’écran, ce qui peuvent utiliser ces méthodes pour filtrer l’arborescence automation. Si votre <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> méthode transferts gestion de modèle à un homologue de sous-élément, l’homologue de sous-élément <xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A> méthode peut retourner la valeur false pour masquer l’homologue de sous-élément dans l’arborescence automation. Par exemple, le défilement dans une <xref:System.Windows.Controls.ListBox> est gérée par un <xref:System.Windows.Controls.ScrollViewer>et l’homologue automation de <xref:System.Windows.Automation.Peers.PatternInterface?displayProperty=fullName> est retourné par le <xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A> méthode de la <xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer> qui est associé le <xref:System.Windows.Automation.Peers.ListBoxAutomationPeer>. Par conséquent, le <xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A> procédé de la <xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer> retourne `false`, de sorte que la <xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer> n’apparaît pas dans l’arborescence automation.  
  
 Votre homologue automation doit fournir des valeurs par défaut appropriées pour votre contrôle. Notez que XAML qui référence votre contrôle peut substituer vos implémentations homologues de méthodes de base en incluant <xref:System.Windows.Automation.AutomationProperties> attributs. Par exemple, le code XAML suivant crée un bouton qui a deux personnalisé [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] propriétés.  
  
```xaml  
<Button AutomationProperties.Name="Special"   
    AutomationProperties.HelpText="This is a special button."/>  
```  
  
### <a name="implement-pattern-providers"></a>Implémenter des fournisseurs de modèles  
 Les interfaces implémentées par un fournisseur personnalisé sont déclarées explicitement si l’élément propriétaire dérive directement de <xref:System.Windows.Controls.Control>. Par exemple, le code suivant déclare un homologue pour un <xref:System.Windows.Controls.Control> qui implémente une valeur de plage.  
  
```csharp  
public class RangePeer1 : FrameworkElementAutomationPeer, IRangeValueProvider { }  
```  
  
```vb  
Public Class RangePeer1  
    Inherits FrameworkElementAutomationPeer  
    Implements IRangeValueProvider  
End Class  
```  
  
 Si le contrôle propriétaire dérive un type spécifique de contrôle tel que <xref:System.Windows.Controls.Primitives.RangeBase>, l’homologue peut être dérivé d’une classe homologue dérivée équivalente. Dans ce cas, l’homologue dériverait de <xref:System.Windows.Automation.Peers.RangeBaseAutomationPeer>, qui fournit une implémentation de base de <xref:System.Windows.Automation.Provider.IRangeValueProvider>. Le code suivant illustre la déclaration d’un tel homologue.  
  
```csharp  
public class RangePeer2 : RangeBaseAutomationPeer { }  
```  
  
```vb  
Public Class RangePeer2  
    Inherits RangeBaseAutomationPeer  
End Class  
```  
  
 Pour un exemple d’implémentation, consultez [contrôle personnalisé NumericUpDown avec thème et prise en charge d’UI Automation, exemple](http://go.microsoft.com/fwlink/?LinkID=160025).  
  
### <a name="raise-events"></a>Déclencher des événements  
 Les clients Automation peuvent s’abonner à des événements automation. Contrôles personnalisés doivent signaler les modifications apportées à l’état du contrôle en appelant le <xref:System.Windows.Automation.Peers.AutomationPeer.RaiseAutomationEvent%2A> (méthode). De même, lorsqu’une valeur de propriété change, appelez le <xref:System.Windows.Automation.Peers.AutomationPeer.RaisePropertyChangedEvent%2A> (méthode). Le code suivant montre comment obtenir l’objet homologue à partir du code de contrôle et appeler une méthode pour déclencher un événement. Une optimisation, le code détermine s’il existe des écouteurs pour ce type d’événement. Déclenche l’événement uniquement lorsqu’il existe des écouteurs évite les charges mémoire inutile et permet au contrôle de rester réactif.  
  
 [!code-csharp[CustomControlNumericUpDown#RaiseEventFromControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#raiseeventfromcontrol)]
 [!code-vb[CustomControlNumericUpDown#RaiseEventFromControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#raiseeventfromcontrol)]  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble UI Automation](../../../../docs/framework/ui-automation/ui-automation-overview.md)   
 [Contrôle personnalisé NumericUpDown avec thème et prise en charge d’UI Automation, exemple](http://go.microsoft.com/fwlink/?LinkID=160025)   
 [Implémentation de fournisseur côté serveur UI Automation](../../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)