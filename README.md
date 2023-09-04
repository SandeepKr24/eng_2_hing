## Hi!
#### Here, I will explain how to use the model.

But first I would like to talk about the data.  
I tried to find a suitable dataset from the web but couldn't find any. So, I created my own. This is the reason why it does not contain my tuples (only 64).

So, to run the model you would have to first download it from google drive (link: https://drive.google.com/drive/folders/1cb1CmmQ9TGIzapWyRwVLfCPKgWIhN_Pz?usp=sharing).  I would recommend that you store it in the root directory.  
Next, load it into your notebook.
The code snippet for this is: 
```
model_name = "facebook/mbart-large-50"
upd_model = MBartForConditionalGeneration.from_pretrained("./fine-tuned-model")
tokenizer = MBartTokenizer.from_pretrained(model_name)
```
Running the above code would load the tuned model into your notebook, and it can now be used to translate any text.  
You can either manually type in the text or read it from a file.
eg- 
```
input_text = "Definitely share your feedback in the comment section"
input_ids = tokenizer.encode("en_" + input_text_one, return_tensors="pt", max_length=1024, padding="max_length", truncation=True)
translation = upd_model.generate(input_ids_one, max_length=1024, num_return_sequences=1, decoder_start_token_id=upd_model.config.decoder_start_token_id)
translated_text = tokenizer.decode(translation_one[0], skip_special_tokens=True)
print(translated_text)
```
That is all, thank you for visiting.
