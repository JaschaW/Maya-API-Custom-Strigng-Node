# -------------------------------------------------------------------------------------------------------------------- #
# Title           : jwCustom_Node
# Description     : This script is to serve as a template to create future nodes of similar fashion
# Author          : Jascha Wohlkinger
# Date            : 2018-05-17
# Version         : 1.0
# Python Version  : 2.7.11
# -------------------------------------------------------------------------------------------------------------------- #

import sys
import maya.OpenMaya as OpenMaya
import maya.OpenMayaMPx as OpenMayaMPx

# ==================================================================================================================== #
# Custom Node
# ==================================================================================================================== #

# Basic Parameters for node creation
nodeName = "jwCustomNode"
nodeID = OpenMaya.MTypeId(0x100fff)

# -------------------------------------------------------------------------------------------------------------------- #

# Class to create Custom Node
class CustomNode(OpenMayaMPx.MPxNode):
    def __init__(self):
        OpenMayaMPx.MPxNode.__init__(self)

# -------------------------------------------------------------------------------------------------------------------- #

def nodeCreator():
    return OpenMayaMPx.asMPxPtr(CustomNode())

# -------------------------------------------------------------------------------------------------------------------- #

def nodeInitializer():

    # Get Input Path
    # Create function set for input string attribute
    input_path_string = OpenMaya.MFnStringData().create("<FilePathIn>")
    input_directory_attribute = OpenMaya.MFnTypedAttribute()
    CustomNode.input_directory = input_directory_attribute.create("File_Input", "fileIn", OpenMaya.MFnData.kString,
                                                                  input_path_string)
    # Attaching input Attributes
    CustomNode.addAttribute(CustomNode.input_directory)

    # Get Output Path
    # Create function set for output string attribute
    output_path_string = OpenMaya.MFnStringData().create("<FilePathOut>")
    output_directory_attribute = OpenMaya.MFnTypedAttribute()
    CustomNode.output_directory = output_directory_attribute.create("File_Output", "fileOut", OpenMaya.MFnData.kString,
                                                                    output_path_string)
    # Attaching output Attributes
    CustomNode.addAttribute(CustomNode.output_directory)

# -------------------------------------------------------------------------------------------------------------------- #

# Initialize the script plugin
def initializePlugin(mobject):
    mPlugin = OpenMayaMPx.MFnPlugin(mobject)
    try:
        mPlugin.registerNode(nodeName, nodeID, nodeCreator, nodeInitializer)
    except:
        sys.stderr.write("Failed to register node: {}".format(nodeName))

# -------------------------------------------------------------------------------------------------------------------- #

# Uninitialize the script plugin
def uninitializePlugin(mobject):
    mPlugin = OpenMayaMPx.MFnPlugin(mobject)
    try:
        mPlugin.deregisterNode(nodeID)
    except:
        sys.stderr.write("Failed to deregister node: {}".format(nodeName))

# -------------------------------------------------------------------------------------------------------------------- #
