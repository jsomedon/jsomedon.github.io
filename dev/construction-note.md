# construction note

## files && branch scheme

```
_____________ <master> : generated site files in root dir

_____________ <draft> : draft files in draft dir
                \______ <dev> : tools & files using draft files
                                to generate and publish site files
                                in dev dir
```

I am tracking draft with a seperate branch so I can `git log` to check my authoring frequency.

## todo

- basic feature
    - searching
        - database
        - search logic
    - index page
        - database
        - generation logic
    - template
    - building
    - testing
    - publishing
    - repo utility
        - hook to auto rebase `dev` on each commit in `draft`
- enhancement
    - cache controll (maybe it's a basic feature...)
    - mobile support (css layout, overall design.. this should be huge)
    - that cool animation on scroll event you see on apple product page (purely eyecandy)

## page structure && template design scheme

