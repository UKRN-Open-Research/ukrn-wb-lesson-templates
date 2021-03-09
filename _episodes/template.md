---
title:  # title of the episode
teaching: # time required to teach (minutes)
exercises: # time required for participants to do the activities (minutes)
duration: # duration for a break, not needed if teaching/exercises are present (minutes)
# summary of the episode content for displaying on the schedule page
summary: >-
questions: # list of questions we are trying to answer
objectives: # list of learning outcomes
keypoints: # list of take-home points
is-break:  # whether this episode is a break (has different presentation)
ukrn_wb_rules: # list of rules for the UKRN Workshop Builder tool
    - allow-multiple # when dragged into the schedule, create a new instance
    - hidden # don't show in the builder
    - template # is a template
    - undeletable # cannot be removed using the tool

ukrn_wb:
    - fields_structure:
        - name # Pretty name of the field
        - type # Data type
        - help # Help text
        - is_array # Whether data is a list
        - is_required # Whether field is required
        - format # Formatting details for data
        - special # Special information for deriving data e.g. options list
    - fields:
        - title:
            - Title
            - string
            - >-
                The title for the episode
            - false
            - true
            - null
            - null
        - teaching:
            - Teaching time
            - number
            - >-
                The number of minutes teaching time required
            - false
            - false
            - null
            - null
        - exercises:
            - Working time
            - number
            - >-
                The number of minutes required to complete any exercises
            - false
            - false
            - null
            - null
        - duration:
            - Duration
            - number
            - >-
                Additional duration not accounted for by teaching or exercise time (e.g. break time)
            - false
            - false
            - null
            - null
        - summary:
            - Summary
            - string
            - >-
                Short text summarising what happens in the episode
            - false
            - false
            - long
            - null
        - questions:
            - Questions
            - string
            - >-
                Questions which will be addressed during the episode
            - true
            - false
            - long
            - null
        - objectives:
            - Objectives
            - string
            - >-
                Learning outcomes for the episode
            - true
            - false
            - long
            - null
        - keypoints:
            - Key points
            - string
            - >-
                The take-home points for the episode
            - true
            - false
            - long
            - null
        - is-break:
            - Break
            - boolean
            - >-
                Whether this episode is a break (breaks look different in the schedule)
            - false
            - false
            - null
            - null
        - ukrn_wb_rules:
            - UKRN Workshop Builder rules
            - string
            - >-
                List of special rules to apply when this episode is processed by the UKRN Workshop Builder
            - true
            - false
            - ukrn-wb-rules
            - ['allow-multiple', 'hidden', 'template']
---

