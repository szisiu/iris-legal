# iris-legal

Public policy pages for the IRIS Instagram application, served via GitHub Pages.

Meta requires a privacy policy, terms of service, and data deletion URL before an app
can be published (switched from Development to Live). These pages exist to satisfy
that, and are kept out of the application repo deliberately — they are public static
content with a different deploy cadence and no build step.

| File | Meta App Dashboard field |
|---|---|
| `privacy.html` | Settings → Basic → Privacy Policy URL |
| `terms.html` | Settings → Basic → Terms of Service URL |
| `data-deletion.html` | Settings → Basic → Data Deletion Instructions URL |

`.nojekyll` is required: GitHub Pages runs Jekyll by default and would drop any file
whose name begins with an underscore.

These are drafts written to Meta's publishing requirements, not legal advice. Have
them reviewed before onboarding paying customers.
