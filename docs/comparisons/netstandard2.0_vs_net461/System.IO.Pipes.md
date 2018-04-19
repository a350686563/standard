# System.IO.Pipes

``` diff
 namespace System.IO.Pipes {
     public sealed class AnonymousPipeClientStream : PipeStream {
+        ~AnonymousPipeClientStream();
     }
     public sealed class AnonymousPipeServerStream : PipeStream {
+        public AnonymousPipeServerStream(PipeDirection direction, HandleInheritability inheritability, int bufferSize, PipeSecurity pipeSecurity);
+        ~AnonymousPipeServerStream();
     }
     public sealed class NamedPipeClientStream : PipeStream {
+        public NamedPipeClientStream(string serverName, string pipeName, PipeAccessRights desiredAccessRights, PipeOptions options, TokenImpersonationLevel impersonationLevel, HandleInheritability inheritability);
+        ~NamedPipeClientStream();
     }
     public sealed class NamedPipeServerStream : PipeStream {
+        public NamedPipeServerStream(string pipeName, PipeDirection direction, int maxNumberOfServerInstances, PipeTransmissionMode transmissionMode, PipeOptions options, int inBufferSize, int outBufferSize, PipeSecurity pipeSecurity);
+        public NamedPipeServerStream(string pipeName, PipeDirection direction, int maxNumberOfServerInstances, PipeTransmissionMode transmissionMode, PipeOptions options, int inBufferSize, int outBufferSize, PipeSecurity pipeSecurity, HandleInheritability inheritability);
+        public NamedPipeServerStream(string pipeName, PipeDirection direction, int maxNumberOfServerInstances, PipeTransmissionMode transmissionMode, PipeOptions options, int inBufferSize, int outBufferSize, PipeSecurity pipeSecurity, HandleInheritability inheritability, PipeAccessRights additionalAccessRights);
+        ~NamedPipeServerStream();
     }
+    public enum PipeAccessRights {
+        AccessSystemSecurity = 16777216,
+        ChangePermissions = 262144,
+        CreateNewInstance = 4,
+        Delete = 65536,
+        FullControl = 2032031,
+        Read = 131209,
+        ReadAttributes = 128,
+        ReadData = 1,
+        ReadExtendedAttributes = 8,
+        ReadPermissions = 131072,
+        ReadWrite = 131483,
+        Synchronize = 1048576,
+        TakeOwnership = 524288,
+        Write = 274,
+        WriteAttributes = 256,
+        WriteData = 2,
+        WriteExtendedAttributes = 16,
+    }
+    public sealed class PipeAccessRule : AccessRule {
+        public PipeAccessRule(IdentityReference identity, PipeAccessRights rights, AccessControlType type);
+        public PipeAccessRule(string identity, PipeAccessRights rights, AccessControlType type);
+        public PipeAccessRights PipeAccessRights { get; }
+    }
+    public sealed class PipeAuditRule : AuditRule {
+        public PipeAuditRule(IdentityReference identity, PipeAccessRights rights, AuditFlags flags);
+        public PipeAuditRule(string identity, PipeAccessRights rights, AuditFlags flags);
+        public PipeAccessRights PipeAccessRights { get; }
+    }
+    public class PipeSecurity : NativeObjectSecurity {
+        public PipeSecurity();
+        public override Type AccessRightType { get; }
+        public override Type AccessRuleType { get; }
+        public override Type AuditRuleType { get; }
+        public override AccessRule AccessRuleFactory(IdentityReference identityReference, int accessMask, bool isInherited, InheritanceFlags inheritanceFlags, PropagationFlags propagationFlags, AccessControlType type);
+        public void AddAccessRule(PipeAccessRule rule);
+        public void AddAuditRule(PipeAuditRule rule);
+        public sealed override AuditRule AuditRuleFactory(IdentityReference identityReference, int accessMask, bool isInherited, InheritanceFlags inheritanceFlags, PropagationFlags propagationFlags, AuditFlags flags);
+        protected internal void Persist(SafeHandle handle);
+        protected internal void Persist(string name);
+        public bool RemoveAccessRule(PipeAccessRule rule);
+        public void RemoveAccessRuleSpecific(PipeAccessRule rule);
+        public bool RemoveAuditRule(PipeAuditRule rule);
+        public void RemoveAuditRuleAll(PipeAuditRule rule);
+        public void RemoveAuditRuleSpecific(PipeAuditRule rule);
+        public void ResetAccessRule(PipeAccessRule rule);
+        public void SetAccessRule(PipeAccessRule rule);
+        public void SetAuditRule(PipeAuditRule rule);
+    }
     public abstract class PipeStream : Stream {
+        public PipeSecurity GetAccessControl();
+        public void SetAccessControl(PipeSecurity pipeSecurity);
     }
 }
```
