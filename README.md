# handledocs
Utilities for handling document dumps: OCR, image processing, etc.

## Example

This code snippet converts pages of a FOIA response received as an image PDF to a list of strings for analysis:  

```
import ocr_utils

foia_response = '1505Deposits.pdf'
ocr_utils.split_pdf(foia_response)

num_page_start = 3
num_page_end = 23
all_text = []

# OCR every page in the document from num_page_start to num_page_end 
# and store the result in all_text
for page in range(num_page_start, num_page_end + 1):
    indiv_filename = "{}.{}.pdf".format(ocr_utils.get_stem(foia_response), page)
    
    tmp_filename = ocr_utils.rotate_pdf(indiv_filename)
    tmp_image = ocr_utils.convert_to_png(tmp_filename)
    all_text.append(ocr_utils.ocr_image(tmp_image))
```
