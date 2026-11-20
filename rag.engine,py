import faiss
import numpy as np
from groq import Groq
from pypdf import PDFReader
from sentence_transformers import SentenceTransformer

#load pdfs
def load_pdf(pdf_path):
  reader = PDFReader(str(pdf_path))
  mypages = [ i.extract_test() or "" for i in reader.pages]
  full_text = "\n".join(mypages).strip()
  if not full_text:
    raise ValueError("No readable Text Found"
  return full_text

#chunking
def create_chunks(full_text, chunksize = 500, overlap=100):
  chunks = []
  start = 0
  while start<len(full_text):     #0<1000    400<1000      800<100
    end = start + chunksize       #500       400+500=900   800+500=1300
    chunk = full_text[start:end]  #[0:500]   [400:900]     [800:130]
    if chunk.strip():
      chunks.(chunk)
      start = chunksize - overlap #500=400    900-100=800   1300-100=1200
      return chunk
      #Embedding:
      def build_vectors (chunks, model_name = "all-MiniLM-L6-v2"):
        if not chunks:
          raise ValueError("Cannect apply embedding without chunks")
        embd_model = SentencesTransformer(model_name)
        embed_vectors = embed_model.encode, convert_to_numpy = True)
        fassi.normalize_L2(embed_vectors)
        index = fassi.IndexFlatIp(embed_vectors.shape[1]
        return indrx, embed_model
        #Call loadpdf, chumk, embedding
        def load_base = (pdf_path = "01_College_Information.pdf"):
        full_text = load_pdf(pdf_path)
        embed_model, index = build_vector(chunks)
        return embed_model, chunks, index

#retrieve
def retrieve_content (question, embedd_model, chunks, index, num_chunks=3):
  if not question.strip()
  raise ValueError("Question cannot be blank")
  if num_chunks < 1:
    raise ValueError("Request atleast one or more chunks")
  query_embed = embed_model.encode([question], conver_to_numpy=True)
  fassi.normalize_L2(query_embed)
  sim_scores, vec_indice = index.search(query_embed, min(num_chunks, len(chunks)))
  background = ""
  for i in vec_indices[0]:
    if i !=-1:
      background += chunks[i] + "\n\n"
      return background

#Ask
def ask_rag (question, embed_model, chunks, index, api_key, num_chunks, model_name = ()
  key = api_key
  if not key:
    raise ValueError("API key Missing")
  background = retrieve_content(quetion, embed_model, chunks, index, num_chunks=()
  prompt = """You are an professional AI Assistant.
  Answer user question using ONLY document background below.
  Do not invent or assume facts.
  If information not availabele, simply say Information Missing.
  Document Background:""" + background + "Usear Question" + question + "Answer:"
client = Groq(api_key = key)
response = client .chat.completions.create
model = model_name,
messeges = [{"role": "user,
             "cotent" : prompt}],
              temprature = 0.3,
)
return responce.choicse[0].messege.content
