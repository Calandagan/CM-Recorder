# Skill activation consistency

This view compares owned skills with recorded activations on the selected course.
It sorts the lowest observed activation frequencies first. It is a descriptive
history, **not an activation probability, skill ranking or explanation of every miss**.

## Counting

- One observation per exact owned skill ID per runner-start. Three runners in one
  race can contribute three observations, not three races.
- Repeated activation events or duplicate inventory entries do not inflate counts.
- Observed frequency = starts with a recorded activation / assessable starts.
- Missing ownership data excludes that runner-start from skill denominators.
- Missing/unusable replay, activation or result evidence makes an absence Unknown;
  unknown observations do not reduce the percentage.
- Fewer than five observed starts is labeled **Small sample**. This threshold is
  a caution label, not a claim of statistical confidence above five starts.

## Controls

Filter by at least one missing activation, catalog mismatch, unconfirmed reason,
or all observed skills. Set the minimum observed starts, choose your runners or
all runners, and optionally include green passives. Green passives are excluded by default.
The response is capped at the 200 lowest frequencies; coverage and totals are shown.

The runner inspector also has **Activation evidence** alongside category/search filters.
Changing these filters does not alter recordings or their exports.

## Explanations and limitations

Static known race/runner facts can be compared with current Global catalog requirements:
distance/category, standard distance, running style, surface, direction, weather,
going, season, course and motivation. Unknown codes and unsupported dynamic conditions
remain unknown. Estimated distance cannot confirm a mismatch.

Example: a skill requiring Sprint has no recorded activation in a known Mile race.
If every alternative requirement is excluded by known static evidence, the view
reports **current catalog mismatch** and explains the incompatible facts.

The catalog is current, not a historical trace of every internal condition check.
If activation was actually recorded, that positive evidence takes precedence even
when the current catalog appears incompatible. Otherwise an unproven reason stays
**unconfirmed**: the program does not invent a wisdom/RNG, positioning or blocking cause.

Different skill IDs are not merged merely because their names or upgrade families
look similar. Global does not normally provide an authoritative list explaining
every non-activation; this analysis does not manufacture one.
