# Industrial AI Personal Site Design

## Goal

Configure the new al-folio site as an English-language professional profile for Siliang Lu that balances academic research credibility with an industry portfolio. The primary audiences are academic collaborators, recruiters, potential partners, and technical readers.

## Positioning

The homepage will present Siliang Lu as a Senior Expert at Bosch Corporate Research leading industrial-AI projects across business units. Its central themes are control and optimization, time-series analysis, and applications in mobility and energy. The copy will emphasize cross-functional leadership and scalable AI solutions that achieve business goals or reduce cost.

## Information Architecture

- **Home (`_pages/about.md`)**: headline, concise professional biography, research domains, selected industrial-AI case studies, selected publications, and social/contact links.
- **About**: expand the career narrative, research interests, and cross-functional leadership story within the homepage/about experience supplied by al-folio.
- **Projects (`_projects/`)**: named Bosch and business-unit case studies. Each will state the business problem, AI approach, Siliang's role, and measurable outcome.
- **Publications (`_bibliography/`)**: retain the existing Google Scholar-backed bibliography and curate entries for public presentation.
- **News and CV**: retain only when their content and links are genuine; remove or disable template modules otherwise.

## Site Wiring and Content

- Update `_config.yml` with accurate English site metadata, SEO keywords, description, navigation-compatible feature flags, and a clean public-site presentation.
- Update `_data/socials.yml` with real contact and professional-profile links, removing example and placeholder identities.
- Update `_pages/about.md` with the approved positioning and without starter biography, address, affiliation, or image placeholders.
- Replace starter projects, posts, news, teaching entries, and other demo content only where public replacement content is available. Do not invent credentials, publications, affiliations, project results, or contact details.
- Use al-folio configuration and content collections before considering local overrides. This project will create no `_layouts`, `_includes`, `_sass`, JavaScript, or runtime-asset overrides.

## Case-study Content Contract

Each public project needs these user-provided facts before it can be published:

1. Title and named Bosch/business-unit context.
2. Business problem and scope.
3. AI method or system approach.
4. Siliang's role and collaboration scope.
5. Approved measurable outcome or business impact.
6. Any image, logo, link, and disclosure constraints.

Bosch and business-unit names plus measurable outcomes may be published, as confirmed by the user. The implementation must still flag anything that appears private, customer-confidential, or not explicitly supplied.

## Validation and Error Handling

- Format and lint the edited content.
- Run `bundle exec al-folio upgrade audit --no-fail` to check compatibility.
- Build with `bundle exec jekyll build --baseurl /al-folio`.
- Report missing assets, invalid metadata, dependency failures, broken links, and confidential-information concerns rather than silently substituting fabricated content.

## Out of Scope

- Changes to al-folio plugin-owned layouts, includes, Sass, JavaScript, or runtime behavior.
- Local theme overrides and a custom CSS/Tailwind pipeline.
- Publishing new claims, project facts, personal contact details, or credentials that the user has not provided.
