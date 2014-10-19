# pcn-spec

This document outlines the standard data format for representing PCN (process-chain-network) analysis.

## What is PCN analysis?

[TODO](https://github.com/mjswensen/pcn-spec/issues/1)

## Examples

[TODO](https://github.com/mjswensen/pcn-spec/issues/3)

```js
{
  "metadata": 
  {
    "title": "Pizza Parlor PCN",
    "description": "This PCN represents the different interactions between a pizza restaurant and a customer.",
    "author": "Morgan Young"
  },

  "domains": 
  [
    {
      "id": "GUID_1234",
      "title": "Pizza Restaurant",
      "subtitle": "Provider"
    },

    {
      "id": "GUID_2345",
      "title": "Customer",
      "subtitle": "Customer"
    }
  ],

  "steps": 
  [
    {
      "id": "GUID_3456",
      "title": "travel to restaurant",
      "type": "process",
      "emphasized": false,
      "value_specific": 0,
      "value_generic": 0,
      "predecessors": [],
      "domain": 
      {
        "id": "GUID_2345",
        "region": 
        {
          "type": "independent",
          "with_domain": ""
        }
      },

      "problems": []
    },

    {
      "id": "GUID_4567",
      "title": "wait to be seated",
      "type": "wait",
      "emphasized": false,
      "value_specific": -1,
      "value_generic": 0,
      "predecessors": 
      [
        {
          "id": "GUID_4567",
          "type": "normal_relationship",
          "title": ""
        }
      ],
      "domain": 
      {
        "id": "GUID_2345",
        "region": 
        {
          "type": "surrogate",
          "with_domain": "GUID_1234"
        }
      },

      "problems": []
    },

    {
      "id": "GUID_5678",
      "title": "seat customer",
      "type": "process",
      "emphasized": false,
      "value_specific": 0,
      "value_generic": 0,
      "predecessors": 
      [
        {
          "id": "GUID_4567",
          "type": "normal_relationship",
          "title": ""
        }
      ],
      "domain": 
      {
        "id": "GUID_1234",
        "region": 
        {
          "type": "direct_TODO",
          "with_domain": "GUID_2345"
        }
      },

      "problems": []
    },

    {
      "id": "GUID_6789",
      "title": "review nenu",
      "type": "process",
      "emphasized": false,
      "value_specific": 1,
      "value_generic": 0,
      "predecessors": 
      [
        {
          "id": "GUID_5678",
          "type": "normal_relationship",
          "title": ""
        }
      ],
      "domain": 
      {
        "id": "GUID_2345",
        "region": 
        {
          "type": "surrogate",
          "with_domain": "GUID_1234"
        }
      },

      "problems": []
    },

    {
      "id": "GUID_78910",
      "title": "create order",
      "type": "process",
      "emphasized": false,
      "value_specific": 1,
      "value_generic": 0,
      "predecessors": 
      [
        {
          "id": "GUID_6789",
          "type": "normal_relationship",
          "title": ""
        }
      ],
      "domain": 
      {
        "id": "GUID_2345",
        "region": 
        {
          "type": "direct",
          "with_domain": "GUID_1234"
        }
      },

      "problems": []
    },

    {
      "id": "GUID_78911",
      "title": "wait for pizza",
      "type": "wait",
      "emphasized": false,
      "value_specific": -1,
      "value_generic": 0,
      "predecessors": 
      [
        {
          "id": "GUID_78910",
          "type": "normal_relationship",
          "title": ""
        }
      ],
      "domain": 
      {
        "id": "GUID_2345",
        "region": 
        {
          "type": "surrogate",
          "with_domain": "GUID_1234"
        }
      },

      "problems": []
    },

    {
      "id": "GUID_78912",
      "title": "eat pizza",
      "type": "process",
      "emphasized": false,
      "value_specific": 2,
      "value_generic": 0,
      "predecessors": 
      [
        {
          "id": "GUID_78911",
          "type": "normal_relationship",
          "title": ""
        },

        {
          "id": "GUID_78917",
          "type": "normal_relationship",
          "title": ""
        }
      ],
      "domain": 
      {
        "id": "GUID_2345",
        "region": 
        {
          "type": "surrogate",
          "with_domain": "GUID_1234"
        }
      },

      "problems": []
    },

    {
      "id": "GUID_78913",
      "title": "develop recepies",
      "type": "divergent_process",
      "emphasized": false,
      "value_specific": 0,
      "value_generic": -1,
      "predecessors": [],
      "domain": 
      {
        "id": "GUID_1234",
        "region": 
        {
          "type": "independent",
          "with_domain": ""
        }
      },

      "problems": []
    },

    {
      "id": "GUID_78914",
      "title": "preheat ovens",
      "type": "process",
      "emphasized": false,
      "value_specific": 0,
      "value_generic": -1,
      "predecessors": [],
      "domain": 
      {
        "id": "GUID_1234",
        "region": 
        {
          "type": "independent",
          "with_domain": ""
        }
      },

      "problems": []
    },

    {
      "id": "GUID_78915",
      "title": "maintain supplies",
      "type": "process",
      "emphasized": false,
      "value_specific": 0,
      "value_generic": -2,
      "predecessors": [],
      "domain": 
      {
        "id": "GUID_1234",
        "region": 
        {
          "type": "independent",
          "with_domain": ""
        }
      },

      "problems": []
    },

    {
      "id": "GUID_78916",
      "title": "assemble and cook pizza",
      "type": "process",
      "emphasized": false,
      "value_specific": 0,
      "value_generic": -1,
      "predecessors": 
      [
        {
          "id": "GUID_78913",
          "type": "loose_temporal_relationship",
          "title": ""
        },

        {
          "id": "GUID_78914",
          "type": "loose_temporal_relationship",
          "title": ""
        },

        {
          "id": "GUID_78915",
          "type": "loose_temporal_relationship",
          "title": ""
        },

        {
          "id": "GUID_78910",
          "type": "normal_relationship",
          "title": ""
        }
      ],
      "domain": 
      {
        "id": "GUID_1234",
        "region": 
        {
          "type": "surrogate",
          "with_domain": "GUID_2345"
        }
      },

      "problems": []
    },

    {
      "id": "GUID_78917",
      "title": "serve pizza",
      "type": "process",
      "emphasized": false,
      "value_specific": 0,
      "value_generic": 0,
      "predecessors": 
      [
        {
          "id": "GUID_78916",
          "type": "normal_relationship",
          "title": ""
        }
      ],
      "domain": 
      {
        "id": "GUID_1234",
        "region": 
        {
          "type": "direct_TODO",
          "with_domain": "GUID_2345"
        }
      },

      "problems": []
    },

    {
      "id": "GUID_78918",
      "title": "prepare check",
      "type": "process",
      "emphasized": false,
      "value_specific": 0,
      "value_generic": 0,
      "predecessors": 
      [
        {
          "id": "GUID_78912",
          "type": "normal_relationship",
          "title": ""
        }
      ],
      "domain": 
      {
        "id": "GUID_1234",
        "region": 
        {
          "type": "surrogate",
          "with_domain": "GUID_2345"
        }
      },

      "problems": []
    },

    {
      "id": "GUID_78919",
      "title": "present check",
      "type": "process",
      "emphasized": false,
      "value_specific": 0,
      "value_generic": 0,
      "predecessors": 
      [
        {
          "id": "GUID_78918",
          "type": "normal_relationship",
          "title": ""
        }
      ],
      "domain": 
      {
        "id": "GUID_1234",
        "region": 
        {
          "type": "direct_TODO",
          "with_domain": "GUID_2345"
        }
      },

      "problems": []
    },

    {
      "id": "GUID_78920",
      "title": "provide payment",
      "type": "process",
      "emphasized": false,
      "value_specific": 0,
      "value_generic": 1,
      "predecessors": 
      [
        {
          "id": "GUID_78919",
          "type": "normal_relationship",
          "title": ""
        }
      ],
      "domain": 
      {
        "id": "GUID_2345",
        "region": 
        {
          "type": "direct_TODO",
          "with_domain": "GUID_1234"
        }
      },

      "problems": []
    },

    {
      "id": "GUID_78921",
      "title": "return home",
      "type": "process",
      "emphasized": false,
      "value_specific": 0,
      "value_generic": 0,
      "predecessors": 
      [
        {
          "id": "GUID_78920",
          "type": "normal_relationship",
          "title": ""
        }
      ],
      "domain": 
      {
        "id": "GUID_2345",
        "region": 
        {
          "type": "independent",
          "with_domain": ""
        }
      },

      "problems": []
    },

    {
      "id": "GUID_78922",
      "title": "eat leftovers",
      "type": "process",
      "emphasized": false,
      "value_specific": 1,
      "value_generic": 0,
      "predecessors": 
      [
        {
          "id": "GUID_78921",
          "type": "loose_temporal_relationship",
          "title": ""
        }
      ],
      "domain": 
      {
        "id": "GUID_2345",
        "region": 
        {
          "type": "independent",
          "with_domain": ""
        }
      },

      "problems": []
    }
  ]
}

## Specification

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
   * analysis.
   * @type {Array.<Object>}
   */
  "domains": [
    {
      /**
       * The id field should contain a unique identifier in string form.
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
  ],

  /**
   * The steps field is where the substance of the analyzed process resides.
   * @type {Array.<Object>}
   */
  "steps": [
    {
      /**
       * A unique identifier for the step.
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
       * relatively more significant.
       * @type {boolean}
       * @optional
       */
      "emphasized": false,

      /**
       * The value_specific field represents the value realization or value
       * potential that the specific beneficiary receives during the step. The
       * value of this field must be an integer (may be negative).
       * @type {number}
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
       * values by dollar signs with negative symbols.
       * @type {number}
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
           * The identifier of the predecessor step.
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
         * The identifier of the domain that the step is associated with.
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
           * - "direct_TODO" - one of the direct interaction regions of the
           *   domain, with preference to the domain's side of the region
           * - "direct" - one of the direct interaction regions of the domain,
           *   in the middle of the region
           * See the with_domain field below.
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
  ]
}
```
