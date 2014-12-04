# pcnspec

This document outlines the standard data format for representing PCN (process-chain-network) analysis.

## What is PCN analysis?

Process Chain Network (PCN) Analysis helps document, diagnose, and improve interactive business processes.  Dr. Scott Sampson, Professor of Service Operations and Business Management at Brigham Young University's Marriott School of Management, describes PCN Analysis as follows:

"The purpose of PCN Analysis is to improve service business processes by systematically documenting the processes, assessing value coming from process components, identifying problem areas, and methodically generating process improvement alternatives.

"PCN Analysis begins by documenting an interactive business process.  This includes identifying which aspects of the process contribute to:

* customer value,
* customer costs (including psychological costs of effort, waiting, etc.),
* provider costs (labor or other resources),
* provider revenue potential,
* risks of process failure, including identifying potential causes of process failure.

"PCN Analysis evaluates the current process configuration and identifies means for process improvement.  The goals of PCN Analysis include:

1. Provide a lean process that delivers maximum value at minimum costs.
2. Provide a robust process that has a low likelihood of failure even when faced with unusual customer variability.
3. Provide an agile process that efficiently and effectively accommodates varying customer needs, so that individual customers are neither over-served nor under-served.
4. Provide a feasible process that can be implemented with the resources and skill sets of both the provider and the customers.
5. Provide an understandable process that can reasonably be communicated to employees and customers.

"In summary, PCN Analysis is a process diagramming technique coupled with principles and methods for analyzing processes and systematically identifying improvement opportunities.  PCN Analysis is founded in state-of-the-art science of service design based on the work of leading management researchers."

Using this standard data format for representing data collected through PCN Analysis, business managers can better interpret the data with any array of products that implement this standard.  This will lead to better interactive business process designs.

## Examples

For complete examples of the standard that use real-world data, please see the [examples](https://github.com/pcnsuite/pcnspec/tree/master/examples) folder of this repository.

## Validation

A PCN Spec validation tool is separately developed and maintained at [pcnlint](https://github.com/pcnsuite/pcnlint). Use pcnlint to ensure JSON is proper according to this specification.

## Specification

### Top Level

```js
/**
 * PCN data specification
 * @version 1.0
 * @author Philip BoBo
 * @author Brooke Frandsen
 * @author Roy Hemmert
 * @author Matthew Swensen
 * @author Morgan Young
 */

{
  /**
   * The optional metadata field is for additional information about the PCN
   * analysis. The fields within the metadata object are flexible and can be
   * defined by the implementer, but the following three fields are recommended:
   * (1) title, (2) description, and (3) author. Other fields that could
   * constitute the metadata object include version and date. Parsers should
   * expect valid JSON in the metadata object if it is provided, but nothing
   * further is enforced.
   * @optional
   */
  "metadata": {
    "title": "",
    "description": "",
    "author": ""
  },

  /**
   * The domains field contains representations of the domains pertaining to the
   * analysis. See "Domain" section below for the format of the objects that
   * populate this field.
   * @type {Array.<Object>}
   */
  "domains": [],

  /**
   * The steps field is where the substance of the analyzed process resides. See
   * the "Steps" section below for the format of the objects that populate this
   * field.
   * @type {Array.<Object>}
   */
  "steps": []
}
```
### Domain ###

The domains field contains representations of the domains pertaining to the analysis.

```js
{
  /**
   * The id field should contain a document-unique identifier in string form.
   * @type {string}
   */
  "id": "",

  /**
   * The title field is used to describe the domain and will usually be
   * filled with the name of the firm or customer segment.
   * @type {string}
   * @example "IKEA"
   */
  "title": "",

  /**
   * The subtitle field can be used for additional information about domain,
   * and will typically denote whether the domain is the provider, the
   * customer, or both.
   * @type {string}
   * @example "Provider"
   */
  "subtitle": ""
}
```

### Steps ###

The steps field is where the substance of the analyzed process resides.

```js

{
  /**
   * A document-unique identifier for the step.
   * @type {string}
   */
  "id": "",

  /**
   * The description of the step.
   * @type {string}
   */
  "title": "",

  /**
   * The type of the step. The value must be one of:
   * - "process" - a standard process step
   * - "decision" - a step that represents a decision
   * - "wait" - a step that requires a waiting period
   *   in graphical representations of the PCN analysis
   * - "divergent_process" - a step that requires human judgment
   * @type {string}
   */
  "type": "",

  /**
   * An optional boolean that indicates whether or not the process is
   * relatively more significant. If not defined, it is assumed to
   * be false.
   * @type {boolean}
   * @optional
   */
  "emphasized": false,

  /**
   * The value_specific field represents the value realization or value
   * potential that the specific beneficiary receives during the step. The
   * value of this field is optional and must be an integer (may be
   * negative). If not defined, it is assumed to be 0 (no or neutral value
   * realization).
   * @type {number}
   * @optional
   * @example 3 (much value realization or potential, perhaps represented by
   *   three smiley faces on a typical PCN diagram)
   * @example 0 (no or neutral value realization)
   * @example -1 (non-monetary cost, perhaps represented graphically by a
   *   frown face)
   */
  "value_specific": 0,

  /**
   * The value_generic field is identical to the value_specific field,
   * except that it represents the value potential or value realization of
   * the generic beneficiary instead of the specific beneficiary. Positive
   * values might be represented graphically by dollar signs, and negative
   * values by dollar signs with negative symbols. This is an optional
   * field and if not defined, it is assumed to be 0.
   * @type {number}
   * @optional
   */
  "value_generic": 0,

  /**
   * The predecessors field defines relationships between the step and other
   * steps. The field is optional and will be omitted for steps that have no
   * predecessors, such as the first step of a process. It will have
   * multiple entries for steps that are a point of convergence in a
   * process.
   * @type {Array.<Object>}
   * @optional
   */
  "predecessors": [
    {
      /**
       * The document-unique identifier of the predecessor step.
       * @type {string}
       */
      "id": "",

      /**
       * The type of relationship with the predecessor. Must be one of:
       * - "normal_relationship" - Typically represented on a PCN diagram by
       *   a solid line.
       * - "loose_temporal_relationship" - Typically represented on a PCN
       *   diagram by a dashed line.
       * @type {string}
       */
      "type": "",

      /**
       * The optional title field provides additional information about the
       * relationship between the steps. For example, "Yes" or "No" might be
       * used for steps that are successors to decision steps.
       * @type {string}
       * @optional
       */
      "title": ""
    }
  ],

  /**
   * The domain field links the step to the domain it is associated with,
   * which are defined in the top-level domains field.
   */
  "domain": {

    /**
     * The document-unique identifier of the domain that the step is associated
     * with.
     * @type {string}
     */
    "id": "",

    /**
     * The process region that the step is in. An object with the two fields
     * outlined below.
     * @type {Object}
     */
    "region": {

      /**
       * The type field identifies the region, and must be one of:
       * - "independent" - the independent processing region of the domain
       * - "surrogate" - one of the surrogate regions of the domain
       * - "direct_leading" - one of the direct interaction regions of the
       *   domain, with preference to the domain's side of the region
       * - "direct_shared" - one of the direct interaction regions of the
       *   domain, in the middle of the region
       * See the with_domain field below.
       * @type {string}
       */
      "type": "",

      /**
       * If the above type field is anything but "independent", the
       * with_domain field is the identifier of the other domain involved
       * in the process. This field determines which of the two surrogate
       * or direct regions the step falls under. If the above type field is
       * "independent", the value of this field should be ignored.
       * @type {string}
       */
      "with_domain": ""
    }
  },

  /**
   * The problems field represents potential issues with the step.
   * @type {Array.<Object>}
   * @optional
   */
  "problems": [
    {
      /**
       * The type of problem must be one of:
       * - "inconvenient"
       * - "confusing"
       * - "difficult"
       * - "likely_to_fail"
       * @type {string}
       */
      "type": "",

      /**
       * The description field builds upon the type field and provides the
       * why or how of the problem.
       * @type {string}
       */
      "description": ""
    }
  ]
}
```
