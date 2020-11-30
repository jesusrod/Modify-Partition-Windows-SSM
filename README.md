# Modify-Partition-Windows-SSM

Copyright (c) 2020. Amazon Web Services Ireland LTD. All Rights Reserved. AWS Enterprise Support Team Name : AutoStopCW-Lambda Version : 1.0.0 Encoded : No Paramaters : None Platform : Any EC2 Associated Files: None Abstract : ReadMe Document Revision History : - 1.0.0 | 07/05/2020 Initial Version Author : Jesus Rodriguez

##################### Automation document Modify-Partition-Windows-SSM.################################################ 
YOU ACKNOWLEDGE AND AGREE THAT THE SCRIPT IS PROVIDED FREE OF CHARGE "AS IS" AND "AVAILABLE" BASIS, AND THAT YOUR USE OF RELIANCE UPON THE APPLICATION OR ANY THIRD PARTY CONTENT AND SERVICES ACCESSED THEREBY IS AT YOUR SOLE RISK AND DISCRETION. IN NO EVENT SHALL THE COPYRIGHT OWNER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
#######################################################################################################################

This SSM automation document will be used whenever you're unable to expland the Windows Partition from script 'SSMEBSResizeWindows'. While trying to execute step 6 for expand volume/partition if this fails, this automation will try and restart the instance trough the API and try and execute this expand volume/partition script again.

These are the steps:

  - name: getInstanceDetails:
  This will retrieve the EBS volume primary EBS volume (Primary Partition on the Windows OS)
  - name: waitForSSMAgentOnline
  This step will try and contact SSM agent from the EC2-Instance
  - name: rebootToMakeItReady
  If the above step fails, it will trigger an EC2-Instance reboot from the API
  - name: waitForInstanceToBeReadyAfterReboot
  Once the instance clears the initialisation tasks, this task will try and contact the SSM agent
  - name: expandpartition
  If the above step is successful, this step will try and expand the partition inside the Windows OS. 

