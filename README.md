# Python-Regular-Expression

## code to find the regular expression pattern for a given string

        from itertools import groupby
        from string import ascii_lowercase

        lower_case = set(ascii_lowercase) # set for faster lookup

        def find_regex(p):
            cum = []
            for c in p:
                if c.isdigit():
                    cum.append("d")
                elif c in lower_case:
                    cum.append("t")
                else:
                    cum.append(c)

            grp = groupby(cum) 
            return ''.join(f'\\{what}{{{how_many}}}' 
                           if how_many>1 else f'\\{what}' 
                           for what,how_many in ( (g[0],len(list(g[1]))) for g in grp))

        pattern = "1example4...whatit.ry2do"

        print(find_regex(pattern))

## website to test regular expression

https://regex101.com/
