import rsdpandoc.builders
import rsdpandoc.globbers
        
env=Environment(tools=['default',rsdpandoc.builders.add_builders])
#env["HavePIL"]=True
#env["HaveWSD"]=True
#env["HaveWebKit"]=True
rsdpandoc.globbers.reveal_layout('scholar/lecture.md',env,"reveal/scholar")
rsdpandoc.globbers.reveal_layout('fabric/lecture.md',env,"reveal/fabric")