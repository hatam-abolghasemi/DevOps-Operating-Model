# Images

*Layer 3 of the [DevOps Operating Model](../README.md): what.*

Rules for container images: where they live, how they are tagged, and how manifests point to them. They extend [naming](naming.md) to the registry, which lives in `cicd`, like the rest of building and delivering ([concerns](concerns.md)).

## Paths

```text
<registry>/<team>/<concern>/<tool>
<registry>/<team>/cicd/apps/<app>
<registry>/<upstream>/<upstream-path>
```

For example `<registry>/devops/cicd/angryduck`, `<registry>/devops/cicd/apps/orders` and `<registry>/dockerhub/library/redis`.

- An image the team builds has the path of its repository. One thing, one name, in Git and in the registry ([belief 9](../1-values/principles.md#9-one-thing-one-name-everywhere)).
- An upstream image is pulled through a proxy cache and keeps its upstream path. The proxy is named after the upstream registry: `dockerhub`, `ghcr`, `quay`, `registry-k8s`.
- The environment never appears in a path or a tag. One image is built once and promoted through `stg` to `prd` unchanged ([belief 11](../1-values/principles.md#11-environments-exist-to-separate-the-different-classes-of-failure-blast-radius)).

## Tags

| Image | Tag | Example |
| --- | --- | --- |
| Tool the team builds | Its release version, from the changelog ([releasing](../4-practices/releasing.md)) | `angryduck:1.4.0` |
| App | The commit it was built from, short SHA | `orders:3f2a9c1` |
| Upstream | Upstream's own version tag | `redis:7.2.4` |

- Tags never move. A pushed tag is never overwritten; a fix is a new tag.
- No `latest`, and no floating tags such as `7` or `stable`. A tag that changes on its own is a default nobody chose ([belief 6](../1-values/principles.md#6-default-is-not-for-production)).

## References

Manifests point to an image by tag and digest:

```yaml
image: <registry>/dockerhub/library/redis:7.2.4@sha256:<digest>
```

The tag tells a person what runs; the digest guarantees it. Both are written, so nothing resolves at deploy time.

## Base images

- Any base OS is allowed. The group that owns the image chooses it.
- The base is pinned by tag and digest in the `FROM` line, the same way manifests reference images.
- Images never run as root ([belief 10](../1-values/principles.md#10-failure-blast-radius-decides-how-much-is-enough)'s security baseline). The Dockerfile sets a non-root `USER`.
