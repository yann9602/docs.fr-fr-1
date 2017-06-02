---
title: "Comment&#160;: cr&#233;er un compl&#233;ment qui est une interface utilisateur | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "créer un complément qui est une interface utilisateur (WPF)"
  - "compléments (WPF), l’interface utilisateur"
  - "créer des compléments d'interface utilisateur (WPF)"
  - "L’interface utilisateur des compléments (WPF), création"
  - "implémenter des compléments d'interface utilisateur (WPF)"
  - "segments de pipeline (WPF), créer des compléments"
ms.assetid: 86375525-282b-4039-8352-8680051a10ea
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# Comment&#160;: cr&#233;er un compl&#233;ment qui est une interface utilisateur
\<?xml version="1.0" encoding="utf-8"?>
\<developerHowToDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Cet exemple montre comment créer un complément qui est une <token>TLA #tla_wpf</token> <token>TLA #tla_ui</token> qui est hébergé par un <token>TLA&#2;tla_wpf</token> application autonome.</para> 
    <para>Le complément est une <token>TLA&#2;tla_ui</token> qui est un <token>TLA&#2;tla_wpf</token> contrôle utilisateur. Le contenu du contrôle utilisateur est un bouton unique qui, lorsqu’on clique dessus, affiche une boîte de message. Le <token>TLA&#2;tla_wpf</token> application autonome héberge le complément <token>TLA&#2;tla_ui</token> en tant que le contenu de la fenêtre principale de l’application.</para> 
    <para> 
      <embeddedLabel>Conditions préalables</embeddedLabel>
    </para>
    <para>cet exemple met en évidence la <token>TLA&#2;tla_wpf</token> extensions pour le <token>dnprdnshort</token> modèle complément qui permet ce scénario et suppose ce qui suit :</para>
    <list class="bullet">
      <listItem>
        <para>connaissance de la <token>dnprdnshort</token> complément modèle, y compris le pipeline de complément et développement de l’hôte. Si vous n’êtes pas familiarisé avec ces concepts, consultez la page \<legacyLink xlink:href="8dd45b02-7218-40f9-857d-40d7b98b850b">des compléments et extensibilité</legacyLink>. Pour obtenir un didacticiel qui montre l’implémentation d’un pipeline, un complément et une application hôte, consultez \<legacyLink xlink:href="694a33c5-a040-450d-aed5-ac49fc88ce61">procédure pas à pas : création d’une Application Extensible</legacyLink>.</para> 
      </listItem> 
      <listItem> 
        <para>Connaissance de la <token>TLA&#2;tla_wpf</token> extensions pour le <token>dnprdnshort</token> -modèle de complément, qui se trouve ici : \<link xlink:href="00b4c776-29a8-4dba-b603-280a0cdc2ade">vue d’ensemble des compléments WPF</link>.</para> 
      </listItem> 
    </list> 
  </introduction> 
  <codeExample> 
    <legacy> 
      <content> 
        <para>Pour créer un complément qui est une <token>TLA&#2;tla_wpf</token> <token>TLA&#2;tla_ui</token> requiert un code spécifique pour chaque segment de pipeline, le complément et l’application hôte.</para> 
        <para> 
          <token>autoOutline</token>
        </para>
      </content>
      <sections>
        <section address="Contract">
          <title>Implémentation du Segment de Pipeline contrat</title>
          <content>
            <para>lorsqu’un complément est un <token>TLA&#2;tla_ui</token>, le contrat pour le complément doit implémenter <codeEntityReference autoUpgrade="true">.INativeHandleContract</codeEntityReference>. Dans l’exemple, <codeInline>IWPFAddInContract</codeInline> implémente <codeEntityReference autoUpgrade="true">.INativeHandleContract</codeEntityReference>, comme illustré dans le code suivant.</para>
            <code language="c#">using System.AddIn.Contract; // INativeHandleContract
using System.AddIn.Pipeline; // AddInContractAttribute

namespace Contracts
{
    /// &lt;summary&gt;
    /// Defines the services that an add-in will provide to a host application.
    /// In this case, the add-in is a UI.
    /// &lt;/summary&gt;
    [AddInContract]
    public interface IWPFAddInContract : INativeHandleContract {}
}</code>
          <code language="vb">Imports System.AddIn.Contract ' INativeHandleContract
Imports System.AddIn.Pipeline ' AddInContractAttribute

Namespace Contracts
    ''' &lt;summary&gt;
    ''' Defines the services that an add-in will provide to a host application.
    ''' In this case, the add-in is a UI.
    ''' &lt;/summary&gt;
    &lt;AddInContract&gt;
    Public Interface IWPFAddInContract
        Inherits INativeHandleContract
        Inherits IContract
    End Interface
End Namespace</code></content>
        </section>
        <section address="AddInViewPipeline">
          <title>Implémentation du Segment de Pipeline de complément vue</title>
          <content>
            <para>, car le complément est implémenté comme une sous-classe de la <codeEntityReference autoUpgrade="true">.FrameworkElement</codeEntityReference> type, la vue de complément doit également sous-classer <codeEntityReference autoUpgrade="true">.FrameworkElement</codeEntityReference>. Le code suivant illustre la vue du complément du contrat, implémentée comme la <codeInline>WPFAddInView</codeInline> classe</para> 
            <code language="c#">using System.AddIn.Pipeline; // AddInBaseAttribute
using System.Windows.Controls; // UserControl

namespace AddInViews
{
    /// &lt;summary&gt;
    /// Defines the add-in's view of the contract.
    /// &lt;/summary&gt;
    [AddInBase]
    public class WPFAddInView : UserControl { }
}</code> 
          <code language="vb">Imports System.AddIn.Pipeline ' AddInBaseAttribute
Imports System.Windows.Controls ' UserControl

Namespace AddInViews
    ''' &lt;summary&gt;
    ''' Defines the add-in's view of the contract.
    ''' &lt;/summary&gt;
    &lt;AddInBase&gt;
    Public Class WPFAddInView
        Inherits UserControl
    End Class
End Namespace</code> 
            <para>Ici, la vue du complément est dérivée de <codeEntityReference autoUpgrade="true">.UserControl</codeEntityReference>. Par conséquent, le complément <token>TLA&#2;tla_ui</token> doit également être dérivée de <codeEntityReference autoUpgrade="true">.UserControl</codeEntityReference>.</para>
          </content>
        </section>
        <section address="AddInSideAdapter">
          <title>Implémentation du Segment de Pipeline de carte Add-In-Side</title>
          <content>
            <para>tandis que le contrat est un <codeEntityReference autoUpgrade="true">.INativeHandleContract</codeEntityReference>, le complément est une <codeEntityReference autoUpgrade="true">.FrameworkElement</codeEntityReference> (comme spécifié par le segment de pipeline de complément, la vue). Par conséquent, le <codeEntityReference autoUpgrade="true">.FrameworkElement</codeEntityReference> doit être converti en un <codeEntityReference autoUpgrade="true">.INativeHandleContract</codeEntityReference> avant de passer par la limite d’isolation. Cette opération est exécutée par l’adaptateur côté complément en appelant <codeEntityReference autoUpgrade="true">M:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter(System.Windows.FrameworkElement)</codeEntityReference>, comme illustré dans le code suivant.</para> 
            <code language="c#">using System; // IntPtr
using System.AddIn.Contract; // INativeHandleContract
using System.AddIn.Pipeline; // AddInAdapterAttribute, FrameworkElementAdapters, ContractBase
using System.Security.Permissions;

using AddInViews; // WPFAddInView
using Contracts; // IWPFAddInContract

namespace AddInSideAdapters
{
    /// &lt;summary&gt;
    /// Adapts the add-in's view of the contract to the add-in contract
    /// &lt;/summary&gt;
    [AddInAdapter]
    public class WPFAddIn_ViewToContractAddInSideAdapter : ContractBase, IWPFAddInContract
    {
        WPFAddInView wpfAddInView;

        public WPFAddIn_ViewToContractAddInSideAdapter(WPFAddInView wpfAddInView)
        {
            // Adapt the add-in view of the contract (WPFAddInView) 
            // to the contract (IWPFAddInContract)
            this.wpfAddInView = wpfAddInView;
        }

        /// &lt;summary&gt;
        /// ContractBase.QueryContract must be overridden to:
        /// * Safely return a window handle for an add-in UI to the host 
        ///   application's application.
        /// * Enable tabbing between host application UI and add-in UI, in the
        ///   "add-in is a UI" scenario.
        /// &lt;/summary&gt;
        public override IContract QueryContract(string contractIdentifier)
        {
            if (contractIdentifier.Equals(typeof(INativeHandleContract).AssemblyQualifiedName))
            {
                return FrameworkElementAdapters.ViewToContractAdapter(this.wpfAddInView);
            }

            return base.QueryContract(contractIdentifier);
        }

        /// &lt;summary&gt;
        /// GetHandle is called by the WPF add-in model from the host application's 
        /// application domain to to get the window handle for an add-in UI from the 
        /// add-in's application domain. GetHandle is called if a window handle isn't 
        /// returned by other means ie overriding ContractBase.QueryContract, 
        /// as shown above.
        /// NOTE: This method requires UnmanagedCodePermission to be called 
        ///       (full-trust by default), to prevent illegal window handle
        ///       access in partially trusted scenarios. If the add-in could
        ///       run in a partially trusted application domain 
        ///       (eg AddInSecurityLevel.Internet), you can safely return a window
        ///       handle by overriding ContractBase.QueryContract, as shown above.
        /// &lt;/summary&gt;
        [SecurityPermissionAttribute(SecurityAction.Demand, Flags = SecurityPermissionFlag.UnmanagedCode)]
        public IntPtr GetHandle()
        {
            return FrameworkElementAdapters.ViewToContractAdapter(this.wpfAddInView).GetHandle();
        }
    }
}</code> 
          <code language="vb">Imports System ' IntPtr
Imports System.AddIn.Contract ' INativeHandleContract
Imports System.AddIn.Pipeline ' AddInAdapterAttribute, FrameworkElementAdapters, ContractBase
Imports System.Security.Permissions

Imports AddInViews ' WPFAddInView
Imports Contracts ' IWPFAddInContract

Namespace AddInSideAdapters
    ''' &lt;summary&gt;
    ''' Adapts the add-in's view of the contract to the add-in contract
    ''' &lt;/summary&gt;
    &lt;AddInAdapter&gt;
    Public Class WPFAddIn_ViewToContractAddInSideAdapter
        Inherits ContractBase
        Implements IWPFAddInContract

        Private wpfAddInView As WPFAddInView

        Public Sub New(ByVal wpfAddInView As WPFAddInView)
            ' Adapt the add-in view of the contract (WPFAddInView) 
            ' to the contract (IWPFAddInContract)
            Me.wpfAddInView = wpfAddInView
        End Sub

        ''' &lt;summary&gt;
        ''' ContractBase.QueryContract must be overridden to:
        ''' * Safely return a window handle for an add-in UI to the host 
        '''   application's application.
        ''' * Enable tabbing between host application UI and add-in UI, in the
        '''   "add-in is a UI" scenario.
        ''' &lt;/summary&gt;
        Public Overrides Function QueryContract(ByVal contractIdentifier As String) As IContract
            If contractIdentifier.Equals(GetType(INativeHandleContract).AssemblyQualifiedName) Then
                Return FrameworkElementAdapters.ViewToContractAdapter(Me.wpfAddInView)
            End If

            Return MyBase.QueryContract(contractIdentifier)
        End Function

        ''' &lt;summary&gt;
        ''' GetHandle is called by the WPF add-in model from the host application's 
        ''' application domain to to get the window handle for an add-in UI from the 
        ''' add-in's application domain. GetHandle is called if a window handle isn't 
        ''' returned by other means ie overriding ContractBase.QueryContract, 
        ''' as shown above.
        ''' NOTE: This method requires UnmanagedCodePermission to be called 
        '''       (full-trust by default), to prevent illegal window handle
        '''       access in partially trusted scenarios. If the add-in could
        '''       run in a partially trusted application domain 
        '''       (eg AddInSecurityLevel.Internet), you can safely return a window
        '''       handle by overriding ContractBase.QueryContract, as shown above.
        ''' &lt;/summary&gt;
        &lt;SecurityPermissionAttribute(SecurityAction.Demand, Flags:=SecurityPermissionFlag.UnmanagedCode)&gt;
        Public Function GetHandle() As IntPtr Implements INativeHandleContract.GetHandle
            Return FrameworkElementAdapters.ViewToContractAdapter(Me.wpfAddInView).GetHandle()
        End Function

    End Class
End Namespace</code> 
            <para>Dans le modèle de complément, où un complément qui retourne un <token>TLA&#2;tla_ui</token> (voir \<link xlink:href="57f274b7-4c66-4b72-92eb-81939a393776">Comment : créer un complément que retourne une interface utilisateur</link>), l’adaptateur du complément convertit le <codeEntityReference autoUpgrade="true">.FrameworkElement</codeEntityReference> à une <codeEntityReference autoUpgrade="true">.INativeHandleContract</codeEntityReference> en appelant <codeEntityReference autoUpgrade="true">M:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter(System.Windows.FrameworkElement)</codeEntityReference>. <codeEntityReference autoUpgrade="true">M:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter(System.Windows.FrameworkElement)</codeEntityReference> doit également être appelé dans ce modèle, bien que vous devez implémenter une méthode depuis laquelle écrire le code pour l’appeler. Cela en remplaçant <codeEntityReference autoUpgrade="true">M:System.AddIn.Pipeline.ContractBase.QueryContract(System.String)</codeEntityReference> et implémentez le code qui appelle <codeEntityReference autoUpgrade="true">M:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter(System.Windows.FrameworkElement)</codeEntityReference> si le code qui appelle <codeEntityReference autoUpgrade="true">M:System.AddIn.Pipeline.ContractBase.QueryContract(System.String)</codeEntityReference> attend un <codeEntityReference autoUpgrade="true">.INativeHandleContract</codeEntityReference>. Dans ce cas, l’appelant sera l’adaptateur côté hôte, qui est présentée dans une sous-section ultérieure.</para>
            <alert class="note">
              <para> Vous devez également substituer <codeEntityReference autoUpgrade="true">M:System.AddIn.Pipeline.ContractBase.QueryContract(System.String)</codeEntityReference> dans ce modèle pour permettre la tabulation entre l’application hôte <token>TLA&#2;tla_ui</token> et complément <token>TLA&#2;tla_ui</token>. Pour plus d’informations, consultez « Limitations des Add-In WPF » dans \<link xlink:href="00b4c776-29a8-4dba-b603-280a0cdc2ade">vue d’ensemble des compléments WPF</link>.</para> 
            </alert> 
            <para>, Car l’adaptateur côté complément implémente une interface qui dérive de <codeEntityReference autoUpgrade="true">.INativeHandleContract</codeEntityReference>, vous devez également implémenter <codeEntityReference autoUpgrade="true">.GetHandle</codeEntityReference>, bien que cette opération soit ignorée lors de la <codeEntityReference autoUpgrade="true">M:System.AddIn.Pipeline.ContractBase.QueryContract(System.String)</codeEntityReference> est remplacée.</para>
          </content>
        </section>
        <section address="HostViewPipeline">
          <title>Implémentation du Segment de Pipeline de vue hôte</title>
          <content>
            <para>dans ce modèle, l’application hôte attend en général que la vue hôte soit une <codeEntityReference autoUpgrade="true">.FrameworkElement</codeEntityReference> sous-classe. L’adaptateur côté hôte doit convertir le <codeEntityReference autoUpgrade="true">.INativeHandleContract</codeEntityReference> à un <codeEntityReference autoUpgrade="true">.FrameworkElement</codeEntityReference> après le <codeEntityReference autoUpgrade="true">.INativeHandleContract</codeEntityReference> dépasse la limite d’isolation. Car une méthode n’est pas appelée par l’application hôte pour obtenir le <codeEntityReference autoUpgrade="true">.FrameworkElement</codeEntityReference>, la vue hôte doit « return » la <codeEntityReference autoUpgrade="true">.FrameworkElement</codeEntityReference> par qui la contient. Par conséquent, la vue hôte doit dériver d’une sous-classe de <codeEntityReference autoUpgrade="true">.FrameworkElement</codeEntityReference> qui peut contenir d’autres <token>TLA&#2;tla_ui #plural</token>, tel que <codeEntityReference autoUpgrade="true">.UserControl</codeEntityReference>. Le code suivant illustre la vue hôte du contrat, implémentée comme la <codeInline>WPFAddInHostView</codeInline> (classe).</para>
            <code language="c#">using System.Windows.Controls; // UserControl

namespace HostViews
{
    /// &lt;summary&gt;
    /// Defines the host's view of the add-in
    /// &lt;/summary&gt;
    public class WPFAddInHostView : UserControl { }
}</code>
          <code language="vb">Imports System.Windows.Controls ' UserControl

Namespace HostViews
    ''' &lt;summary&gt;
    ''' Defines the host's view of the add-in
    ''' &lt;/summary&gt;
    Public Class WPFAddInHostView
        Inherits UserControl
    End Class
End Namespace</code>
          </content>
        </section>
        <section address="HostSideAdapter">
          <title>Implémentation du Segment de Pipeline adaptateur côté hôte</title>
          <content>
            <para>tandis que le contrat est un <codeEntityReference autoUpgrade="true">.INativeHandleContract</codeEntityReference>, l’application hôte attend un <codeEntityReference autoUpgrade="true">.UserControl</codeEntityReference> (comme spécifié par la vue hôte). Par conséquent, le <codeEntityReference autoUpgrade="true">.INativeHandleContract</codeEntityReference> doit être converti en un <codeEntityReference autoUpgrade="true">.FrameworkElement</codeEntityReference> après être passé par la limite d’isolation, avant d’être définie en tant que contenu de la vue hôte (qui dérive de <codeEntityReference autoUpgrade="true">.UserControl</codeEntityReference>).</para> 
            <para>Cette opération est exécutée par l’adaptateur côté hôte, comme indiqué dans le code suivant. </para> 
            <code language="c#">using System.AddIn.Contract; // INativeHandleContract
using System.AddIn.Pipeline; // HostAdapterAttribute, FrameworkElementAdapters, ContractHandle
using System.Windows; // FrameworkElement

using Contracts; // IWPFAddInContract
using HostViews; // WPFAddInHostView

namespace HostSideAdapters
{
    /// &lt;summary&gt;
    /// Adapts the add-in contract to the host's view of the add-in
    /// &lt;/summary&gt;
    [HostAdapter]
    public class WPFAddIn_ContractToViewHostSideAdapter : WPFAddInHostView
    {
        IWPFAddInContract wpfAddInContract;
        ContractHandle wpfAddInContractHandle;

        public WPFAddIn_ContractToViewHostSideAdapter(IWPFAddInContract wpfAddInContract)
        {
            // Adapt the contract (IWPFAddInContract) to the host application's
            // view of the contract (WPFAddInHostView)
            this.wpfAddInContract = wpfAddInContract;

            // Prevent the reference to the contract from being released while the
            // host application uses the add-in
            this.wpfAddInContractHandle = new ContractHandle(wpfAddInContract);

            // Convert the INativeHandleContract for the add-in UI that was passed 
            // from the add-in side of the isolation boundary to a FrameworkElement
            string aqn = typeof(INativeHandleContract).AssemblyQualifiedName;
            INativeHandleContract inhc = (INativeHandleContract)wpfAddInContract.QueryContract(aqn);
            FrameworkElement fe = (FrameworkElement)FrameworkElementAdapters.ContractToViewAdapter(inhc);

            // Add FrameworkElement (which displays the UI provided by the add-in) as
            // content of the view (a UserControl)
            this.Content = fe;
        }
    }
}</code> 
          <code language="vb">Imports System.AddIn.Contract ' INativeHandleContract
Imports System.AddIn.Pipeline ' HostAdapterAttribute, FrameworkElementAdapters, ContractHandle
Imports System.Windows ' FrameworkElement

Imports Contracts ' IWPFAddInContract
Imports HostViews ' WPFAddInHostView

Namespace HostSideAdapters
    ''' &lt;summary&gt;
    ''' Adapts the add-in contract to the host's view of the add-in
    ''' &lt;/summary&gt;
    &lt;HostAdapter&gt;
    Public Class WPFAddIn_ContractToViewHostSideAdapter
        Inherits WPFAddInHostView
        Private wpfAddInContract As IWPFAddInContract
        Private wpfAddInContractHandle As ContractHandle

        Public Sub New(ByVal wpfAddInContract As IWPFAddInContract)
            ' Adapt the contract (IWPFAddInContract) to the host application's
            ' view of the contract (WPFAddInHostView)
            Me.wpfAddInContract = wpfAddInContract

            ' Prevent the reference to the contract from being released while the
            ' host application uses the add-in
            Me.wpfAddInContractHandle = New ContractHandle(wpfAddInContract)

            ' Convert the INativeHandleContract for the add-in UI that was passed 
            ' from the add-in side of the isolation boundary to a FrameworkElement
            Dim aqn As String = GetType(INativeHandleContract).AssemblyQualifiedName
            Dim inhc As INativeHandleContract = CType(wpfAddInContract.QueryContract(aqn), INativeHandleContract)
            Dim fe As FrameworkElement = CType(FrameworkElementAdapters.ContractToViewAdapter(inhc), FrameworkElement)

            ' Add FrameworkElement (which displays the UI provided by the add-in) as
            ' content of the view (a UserControl)
            Me.Content = fe
        End Sub
    End Class
End Namespace</code> 
            <para>Comme vous pouvez le voir, l’adaptateur côté hôte acquiert le <codeEntityReference autoUpgrade="true">.INativeHandleContract</codeEntityReference> en appelant l’adaptateur côté complément <codeEntityReference autoUpgrade="true">M:System.AddIn.Pipeline.ContractBase.QueryContract(System.String)</codeEntityReference> (méthode) (il s’agit du point où la <codeEntityReference autoUpgrade="true">.INativeHandleContract</codeEntityReference> dépasse la limite d’isolation).</para> 
            <para>L’adaptateur côté hôte convertit ensuite le <codeEntityReference autoUpgrade="true">.INativeHandleContract</codeEntityReference> à un <codeEntityReference autoUpgrade="true">.FrameworkElement</codeEntityReference> en appelant <codeEntityReference autoUpgrade="true">(System.AddIn.Contract.INativeHandleContract)</codeEntityReference>. Enfin, le <codeEntityReference autoUpgrade="true">.FrameworkElement</codeEntityReference> est défini comme le contenu de la vue hôte.</para>
          </content>
        </section>
        <section address="AddIn">
          <title>L’implémentation de la macro complémentaire</title>
          <content>
            <para>avec l’adaptateur côté complément et la vue de complément en place, le complément peut être implémenté par une dérivation à partir de la vue de complément, comme indiqué dans le code suivant.</para> 
            <code language="xaml">&lt;addInViews:WPFAddInView
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:addInViews="clr-namespace:AddInViews;assembly=AddInViews"
    x:Class="WPFAddIn1.AddInUI"&gt;

    &lt;Grid&gt;
        &lt;Button Click="clickMeButton_Click" Content="Click Me!" /&gt;        
    &lt;/Grid&gt;

&lt;/addInViews:WPFAddInView&gt;</code> 
            <code language="c#">using System.AddIn; // AddInAttribute
using System.Windows; // MessageBox, RoutedEventArgs

using AddInViews; // WPFAddInView

namespace WPFAddIn1
{
    /// &lt;summary&gt;
    /// Implements the add-in by deriving from WPFAddInView
    /// &lt;/summary&gt;
    [AddIn("WPF Add-In 1")]
    public partial class AddInUI : WPFAddInView
    {
        public AddInUI()
        {
            InitializeComponent();
        }

        void clickMeButton_Click(object sender, RoutedEventArgs e)
        {
            MessageBox.Show("Hello from WPFAddIn1");
        }
    }
}</code> 
          <code language="vb">Imports System.AddIn ' AddInAttribute
Imports System.Windows ' MessageBox, RoutedEventArgs

Imports AddInViews ' WPFAddInView

Namespace WPFAddIn1
    ''' &lt;summary&gt;
    ''' Implements the add-in by deriving from WPFAddInView
    ''' &lt;/summary&gt;
    &lt;AddIn("WPF Add-In 1")&gt;
    Partial Public Class AddInUI
        Inherits WPFAddInView
        Public Sub New()
            InitializeComponent()
        End Sub

        Private Sub clickMeButton_Click(ByVal sender As Object, ByVal e As RoutedEventArgs)
            MessageBox.Show("Hello from WPFAddIn1")
        End Sub
    End Class
End Namespace</code> 
            <para>Dans cet exemple, vous pouvez constater un avantage intéressant de ce modèle : les développeurs de compléments ne doivent implémenter le complément (puisqu’il s’agit du <token>TLA&#2;tla_ui</token> également), au lieu d’une classe et un complément <token>TLA&#2;tla_ui</token>.</para>
          </content>
        </section>
        <section address="HostApp">
          <title>Implémentation de l’Application hôte</title>
          <content>
            <para>par l’adaptateur côté hôte et la vue hôte créés, l’application hôte peut utiliser le <token>dnprdnshort</token> modèle de complément pour ouvrir le pipeline et acquérir une vue hôte du complément. Ces étapes sont indiquées dans le code suivant. </para> 
            <code language="c#">// Get add-in pipeline folder (the folder in which this application was launched from)
string appPath = Environment.CurrentDirectory;

// Rebuild visual add-in pipeline
string[] warnings = AddInStore.Rebuild(appPath);
if (warnings.Length &gt; 0)
{
    string msg = "Could not rebuild pipeline:";
    foreach (string warning in warnings) msg += "\n" + warning;
    MessageBox.Show(msg);
    return;
}

// Activate add-in with Internet zone security isolation
Collection&lt;AddInToken&gt; addInTokens = AddInStore.FindAddIns(typeof(WPFAddInHostView), appPath);
AddInToken wpfAddInToken = addInTokens[0];
this.wpfAddInHostView = wpfAddInToken.Activate&lt;WPFAddInHostView&gt;(AddInSecurityLevel.Internet);

// Display add-in UI
this.addInUIHostGrid.Children.Add(this.wpfAddInHostView);</code> 
          <code language="vb">' Get add-in pipeline folder (the folder in which this application was launched from)
Dim appPath As String = Environment.CurrentDirectory

' Rebuild visual add-in pipeline
Dim warnings() As String = AddInStore.Rebuild(appPath)
If warnings.Length &gt; 0 Then
    Dim msg As String = "Could not rebuild pipeline:"
    For Each warning As String In warnings
        msg &amp;= vbLf &amp; warning
    Next warning
    MessageBox.Show(msg)
    Return
End If

' Activate add-in with Internet zone security isolation
Dim addInTokens As Collection(Of AddInToken) = AddInStore.FindAddIns(GetType(WPFAddInHostView), appPath)
Dim wpfAddInToken As AddInToken = addInTokens(0)
Me.wpfAddInHostView = wpfAddInToken.Activate(Of WPFAddInHostView)(AddInSecurityLevel.Internet)

' Display add-in UI
Me.addInUIHostGrid.Children.Add(Me.wpfAddInHostView)</code> 
            <para>L’application hôte utilise par défaut <token>dnprdnshort</token> code du modèle de complément pour activer le complément, ce qui implicitement retourne la vue hôte à l’application hôte. L’application hôte affiche ensuite la vue hôte (qui est un <codeEntityReference autoUpgrade="true">.UserControl</codeEntityReference>) dans un <codeEntityReference autoUpgrade="true">.Grid</codeEntityReference>.</para> 
            <para>Le code pour le traitement des interactions avec le complément <token>TLA&#2;tla_ui</token> s’exécute dans domaine d’application du complément. Ces interactions sont les suivantes :</para>
            <list class="bullet">
              <listItem>
                <para>gère la <codeEntityReference autoUpgrade="true">.Button</codeEntityReference> <codeEntityReference autoUpgrade="true">.Primitives.ButtonBase.Click</codeEntityReference> événements.</para> 
              </listItem> 
              <listItem> 
                <para>Montrant le <codeEntityReference autoUpgrade="true">: System.Windows.MessageBox</codeEntityReference>.</para> 
              </listItem> 
            </list> 
            <para>Cette activité est complètement isolée de l’application hôte.</para>
          </content>
        </section>
      </sections>
    </legacy>
  </codeExample>
  <relatedTopics>
\<legacyLink xlink:href="8dd45b02-7218-40f9-857d-40d7b98b850b">Compléments et extensibilité</legacyLink>
\<link xlink:href="00b4c776-29a8-4dba-b603-280a0cdc2ade">vue d’ensemble des compléments WPF</link>
</relatedTopics>
</developerHowToDocument>
