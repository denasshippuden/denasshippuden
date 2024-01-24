import os
import shutil
import schedule
import time

def limpar_cache(caminho_cache):
    try:
        if os.path.exists(caminho_cache) and os.path.isdir(caminho_cache):
            shutil.rmtree(caminho_cache)
            os.makedirs(caminho_cache)
            print("Cache limpo com sucesso.")
        else:
            print("Diretório de cache não encontrado.")
    except Exception as e:
        print(f"Erro ao limpar o cache: {str(e)}")
        caminho_cache = "C/Windows/Temp"
        schedule.every().day.at("22:00").do(limpar_cache, caminho_cache)
    while True:
        schedule.run_pending()
        time.sleep(1)
        
