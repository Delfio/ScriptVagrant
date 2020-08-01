require 'dotenv'

vms = {
    "k8s-controller" => {
        :vm_box         => "bento/centos-8.1", 
        :vm_box_version => "202005.21.0", 
        :vm_cpu         => 2, 
        :vm_ram         => 1048, 
        :vm_ip          => "192.168.50.100"
    },
    "k8s-worker-1" => {
        :vm_box         => "bento/centos-8.1",
        :vm_box_version => "202005.21.0",
        :vm_cpu         => 2, 
        :vm_ram         => 1048, 
        :vm_ip          => "192.168.50.102"
    },

}

Vagrant.configure("2") do |config|
    vms.each do | vm_name, vm_params |

        config.vm.define "#{vm_name}" do |vm_item|

            vm_item.vm.hostname    = "#{vm_name}"
            vm_item.vm.box         = "#{vm_params[:vm_box]}"
            vm_item.vm.box_version = "#{vm_params[:vm_box_version]}"

            vm_item.vm.network "private_network", ip: "#{vm_params[:vm_ip]}",
                virtualbox__intnet: true

            vm_item.vm.provider "virtualbox" do |vm_item_vb|

                vm_item_vb.cpus   = vm_params[:vm_cpu]
                vm_item_vb.memory = vm_params[:vm_ram]

            end
        end
    end
end