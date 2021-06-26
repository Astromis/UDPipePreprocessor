# UDPipePreprocessor
Snorkel preprocessor module that allows to use UDPipe. In order to use, it you need a few lines of code

```python

from snorkel_add.UdpipePreprocessor import UDPipePreprocessor

udp = UDPipePreprocessor(text_field="text", doc_field="doc", memoize=True)

@labeling_function(pre=[udp])
def has_main_parts(x):
    poses = []
    for sentence in x.doc:
        poses.extend([x.pos for x in sentence])
    return INTENT if "VERB" in poses and "NOUN" in poses else ABSTAIN

...
```
