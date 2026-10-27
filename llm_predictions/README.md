# Released prediction tables

The prediction tables contain parsed outputs only. They do not contain raw
model responses, rationales, prompts, provider configurations, endpoints,
costs, latency, or token counts.

## Outcome columns

- `outcome_stored` — the original promptfoo outcome used by the paper;
- `outcome_corrected` — corrected only for the Exp. 1 JSON assertion bug;
- `response_status` — `responded` or `no_response`;
- `predicted_number` — parsed sense number;
- `predicted_sid` — sense ID reconstructed using the original seeded shuffle;
  details are given below.

For plain Exp. 1, Phase B, and Exp. 2, `outcome_stored` and
`outcome_corrected` are identical. For `phase_a_json_restricted`, the
difference is documented in [`corrigendum.md`](../corrigendum.md).

The corrected JSON run has 12,540 correct rows and 3,692 format failures;
four malformed responses without an intact `sense_number` field are counted
as format failures. The loose first-integer fallback remains in the plain
parser for 598 Phase A rows (1.91%), 702 Phase B rows (2.13%), 30 Exp. 2 CORE
rows (0.09%), and 109 Exp. 2 EXTENDED rows (0.11%).

`no_response` means that the stored response output is null. Empty-string or
malformed outputs are `responded` rows and may be classified as
`format_failure`. No-response rows retain the original stored classification of `wrong`;
they are not changed to `format_failure` by the JSON correction.

## Runs and keys

- `phase_a_plain_restricted`: 33,760 rows;
- `phase_a_json_restricted`: 33,760 rows;
- `phase_b_plain`: 35,600 rows;
- `exp2_core`: 33,480 rows;
- `exp2_extended`: 100,440 rows.

Exp. 1 joins use `quote_idx`, preserved as a decimal string such as `481.0`.
Exp. 2 joins use `key = lemma::record_id`. `predicted_sid` is reconstructed
using the original seeded shuffle: Exp. 1 uses the `quote_idx` seed and Exp. 2
uses the `record_id` seed, following the released `transform.py` logic. It is
empty when no sense number can be parsed. The reconstruction is validated by
asserting that every corrected row classified as correct has
`predicted_sid == gold_sid`. Exp. 2 novelty `0` is the no-matching-sense
option, not a dictionary sense ID.

