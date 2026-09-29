Task 1 answers for your notes:

Files that exist once for all environments: the four files in base/ (deployment, service, index.html, kustomization).
Values that differ: namespace, replica count, environment label, page text, and prod's resources and image tag.
Where the differences live: each overlay's kustomization.yaml, plus patch-resources.yaml in prod.

Why isn't the ConfigMap named exactly web-content?

Checkpoint answer: Kustomize adds a hash of the file's content to the ConfigMap name and updates every reference to it. When the content changes, the name changes, which is what triggers a rollout in Task 6.

Quick answers for your Task 8 notes:

Merged, not deleted. The patch overrode the request values and added limits. Everything else in the Deployment stayed as in the base.
Prod owns the production resource policy. It lives only in overlays/prod/, so dev and staging are unaffected.
A patch beats a copy. A patch is a few lines describing only the difference, while a copied deployment.yaml must be updated by hand whenever the base changes and can quietly drift.